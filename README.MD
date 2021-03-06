# HTML + CSS @keyframes实现牛顿摆特效

![](./img/newton-cradle.gif)

## HTML 代码
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <link rel="stylesheet" href="css/style.css">
    <title>Newton`s-Animation</title>
</head>
<body>
    <div class="newton-box">
        <span class="circle"></span>
        <span class="circle"></span>
        <span class="circle"></span>
        <span class="circle"></span>
        <span class="circle"></span>
        <div class="bottom-box"></div>
    </div>
</body>
</html>

```

## CSS 代码
```css
body{
    padding: 0;
    margin: 0;
    box-sizing: border-box;
    background-image: linear-gradient(to bottom,#333,#222);
    background-size: cover;
    width: 100%;
    height: 100vh;
}
.newton-box{
    position: absolute;
    display: flex;
    top: 50%;
    left: 50%;
    transform: translate(-50%,-50%);
    border-top: 8px solid #ddd;
    border-left: 8px solid #ddd;
    border-right: 8px solid #ddd;
    padding: 0 50px 20px;
}
.newton-box .circle{
    position: relative;
    display: block;
    width: 1px;
    height: 600px;
    background: #ddd;
    margin: 0 100px;
    transform-origin: top;
}
.circle:before{
    content: '';
    position: absolute;
    bottom: 0;
    width: 200px;
    height: 200px;
    background: radial-gradient(circle at 80px 80px, #b4fef2, #757575);
    border-radius: 50%;
    left: -100px;
}
.circle:nth-child(1),.circle:nth-child(2){
    animation: anim-1 2s linear infinite;
}
.circle:nth-child(4),.circle:nth-child(5){
    animation: anim-2 2s linear infinite 1s;
}
.bottom-box{
    position: absolute;
    width: 1300px;
    height: 60px;
    left: 50%;
    bottom: 0;
    transform: translateX(-50%);
    z-index: -1;

}
.bottom-box:before{
    content: '';
    position: absolute;
    bottom: -10px;
    left: 0;
    width: 100%;
    height: 50px;
    background-color: #ddd;
    transform-origin: left;
    transform: skewX(-41deg);
    z-index: -1;
}
@keyframes anim-1 {
    0%{
        transform: rotate(0deg);
    }
    25%{
        transform: rotate(60deg);
    }
    50%{
        transform: rotate(0deg);
    }
    100%{
        transform: rotate(0deg);
    }
}
@keyframes anim-2 {
    0%{
        transform: rotate(0deg);
    }
    25%{
        transform: rotate(-60deg);
    }
    50%{
        transform: rotate(0deg);
    }
    100%{
        transform: rotate(0deg);
    }
}
```