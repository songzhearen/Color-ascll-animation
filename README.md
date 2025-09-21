# 🎨 彩色 ASCII 动画播放器

> 将 GIF 动画转换为绚丽的彩色 ASCII 艺术，在网页中实时播放

![License](https://img.shields.io/badge/License-MIT-blue.svg)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?logo=javascript&logoColor=black)

## ✨ 项目特色

本项目是基于 [JIEJOE-WEB-Tutorial/015-ascii-animation](https://github.com/JIEJOE-WEB-Tutorial/015-ascii-animation) 的增强版本，**首次实现了真彩色 ASCII 动画效果**！

### 🌈 核心功能

- 🎯 **真彩色渲染** - 保持原始 GIF 的每个像素颜色
- 🎭 **丰富字符集** - 使用 `█▓▒░·°` 等 Unicode 字符表现亮度层次
- 🚀 **高性能播放** - 优化的 HTML/CSS 渲染，流畅动画体验
- 🖼️ **透明度支持** - 完美处理透明背景 GIF
- 🎪 **实时渲染** - 动态生成彩色 HTML 内容

## 🆚 对比原版优势

| 功能特性 | 原版 | 彩色增强版 ✨ |
|---------|------|-------------|
| 颜色支持 | 单色绿色 | 真彩色 RGB |
| 字符集 | `0`, `1`, `.`, `-` | `█▓▒░·°` + 彩色 |
| 渲染方式 | 纯文本 | HTML + CSS |
| 视觉效果 | 单调 | 绚丽多彩 |
| 透明处理 | 基础 | 完整支持 |

## 🚀 快速开始

在 `ascii animation.html` 中修改 GIF 文件名：
```javascript
fetch("your-animation.gif")  // 改为你的 GIF 文件名
```



## 🎨 技术实现

### 彩色渲染算法
```javascript
// 亮度计算 (ITU-R BT.709 标准)
const brightness = (r * 0.299 + g * 0.587 + b * 0.114) / 255;

// 动态 HTML 生成
const color = `rgb(${r}, ${g}, ${b})`;
htmlContent += `<span style="color: ${color};">${char}</span>`;
```

### 字符映射策略
- `█▓` - 最暗区域 (brightness < 0.25)
- `▒░` - 中等区域 (0.25 ≤ brightness < 0.5)
- `·°` - 较亮区域 (0.5 ≤ brightness < 0.75)
- `空格` - 最亮/透明区域 (brightness ≥ 0.75)


## 🔧 自定义配置

### 调整缩放比例
```javascript
scale_nums: 6,  // 减小数值 = 更高精度，增大数值 = 更快性能
```

### 修改动画速度
```javascript
setInterval(() => {
    // 动画帧切换逻辑
}, 60);  // 调整间隔时间 (毫秒)
```

### 自定义字符集
```javascript
const levels = [
    ["█", "▓"],     // 自定义暗部字符
    ["▒", "░"],     // 自定义中间字符  
    ["·", "°"],     // 自定义亮部字符
    [" "]           // 透明/最亮字符
];
```

## 🌟 技术栈

- **前端**: HTML5, CSS3, JavaScript ES6+
- **图像处理**: Canvas API, ImageData API
- **GIF 解析**: gifuct-js 库
- **动画**: CSS + JavaScript 定时器
- **颜色空间**: RGB 色彩模型

## 📊 性能优化

- ✅ 使用 `innerHTML` 批量更新 DOM
- ✅ Canvas 离屏渲染减少重绘
- ✅ 智能跳帧处理大型 GIF
- ✅ 内存管理优化，避免内存泄漏


## 🙏 致谢

- 感谢原作者 **JIEJOE** 的开源分享和创意灵感
- 感谢 [gifuct-js](https://github.com/matt-way/gifuct-js) 提供的 GIF 解析库
- 感谢所有为 ASCII 艺术发展做出贡献的开发者们

---

<div align="center">

**如果这个项目对你有帮助，请给个 ⭐️ Star 支持一下！**

Made with ❤️ by developers who love ASCII art

</div>