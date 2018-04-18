<template>
    <div class="creatives">
        <h1>广告创意</h1>
        <div class="top">
            <h3>落地页</h3>
             <label for="">着陆页地址:<input type="text" placeholder="请设置广告名称"/><span>预览</span></label>
        </div>
        <div class="middle">
            <h3>上传创意</h3>
            <div class="spans">
                <span>创意1</span>
                <span>创意2</span>
                <span>+添加创意</span>
            </div>
               <el-upload
                    class="avatar-uploader"
                    action="http://localhost:9000/dsp-creative/creative/upload"
                    :show-file-list="false"
                    :on-success="handleAvatarSuccess"
                    :before-upload="beforeAvatarUpload">
                    <img v-if="imageUrl" :src="imageUrl" class="avatar">
                    <i v-else class="el-icon-plus avatar-uploader-icon"></i>
               </el-upload>
             <p>JPG/JPEG,小于30KB</p>
        </div>
        <div class="bottom">
            <label for="">广告文案<input type="text" placeholder="请设置广告名称"><span>0</span>/<span>18</span></label>
             <label for="">监听广告<input type="text" placeholder="请设置广告名称"></label>

        </div>
    </div>
</template>
<script>
export default {
     data() {
      return {
        imageUrl: ''
      };
    },
    methods: {
      handleAvatarSuccess(res, file) {
        this.imageUrl = URL.createObjectURL(file.raw);
      },
      beforeAvatarUpload(file) {
        const isJPG = file.type === 'image/jpeg';
        const isLt2M = file.size / 1024 / 1024 < 2;

        if (!isJPG) {
          this.$message.error('上传头像图片只能是 JPG 格式!');
        }
        if (!isLt2M) {
          this.$message.error('上传头像图片大小不能超过 2MB!');
        }
        return isJPG && isLt2M;
      }
    }
}
</script>
<style lang=less scoped>
    .creatives{
        width: 100%;
        height: 100%;
        h1{
            width:100%;
            height: 50px;
            line-height: 50px;
        }
               .top{
           margin-top:10px;
           h3{
               font-size: 20px;
           }
           label{
               display: block;
               color:#333;
               margin-top:10px;
               font-size: 14px;
               input{
                   margin-left: 5px;
                   border: 1px solid #ddd;
                   border-radius: 5px;
                   width:500px;
                   height: 30px;
                   padding-left: 10px;
               }
               span{
                   margin-left: 5px;
                   color:#333;
               }
           }
       }
       .spans{
           width:100%;
           height: 100px;
           span{
               float: left;
               width: 100px;
               height: 50px;
               line-height: 50px;
               text-align: center;
               border-bottom: 1px solid #ccc;

           }
       }
        .middle p{
            color:#ccc;
            font-size: 14px;
        }
        .bottom{
            margin-top: 20px;
            label{
               display: block;
               color:#333;
               margin-top:10px;
               font-size: 14px;
               input{
                   margin-left: 5px;
                   border: 1px solid #ddd;
                   border-radius: 5px;
                   width:500px;
                   height: 30px;
                   padding-left: 10px;
               }
               span{
                   margin-left: 5px;
                   color:#333;
               }
           }
        }

.avatar-uploader .el-upload {
    border: 1px dashed #d9d9d9;
    border-radius: 6px;
    cursor: pointer;
    position: relative;
    overflow: hidden;
  }
  .avatar-uploader .el-upload:hover {
    border-color: #409EFF;
  }
  .avatar-uploader-icon {
    font-size: 28px;
    color: #8c939d;
    width: 178px;
    height: 178px;
    line-height: 178px;
    text-align: center;
  }
  .avatar {
    width: 178px;
    height: 178px;
    display: block;
  }
      
    }
</style>


