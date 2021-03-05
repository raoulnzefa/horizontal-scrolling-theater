# Horizontal Scrolling Theater with Vue.js

[![Photo](https://raw.githubusercontent.com/rayc2045/horizontal-scrolling-theater/master/src/assets/demo/01.png)](https://dribbble.com/raychangdesign)
[![Photo](https://raw.githubusercontent.com/rayc2045/horizontal-scrolling-theater/master/src/assets/demo/02.png)](https://dribbble.com/raychangdesign)
[![Photo](https://raw.githubusercontent.com/rayc2045/horizontal-scrolling-theater/master/src/assets/demo/03.png)](https://dribbble.com/raychangdesign)

> 以前就想過要做一個展示電影的頁面，這次使用 Vue 3 搭配 GSAP，並結合自己收藏的 46 部藍光電影所做成的 API 做串接，達成能夠橫向捲動的電影購物頁面。實作上，除了藉由 CSS 屬性 `relative` 搭配 GSAP 來調整元素的 `left` 值來實現橫向捲動的功能，另外在點擊「加入購物車」按鈕時，透過抓取當下電影封面位置和設計移動軌跡，做出漂亮的放入購物車動畫，以及使用 Vue 的 `watch` API 監視購物車資料，從購物車新增或移除電影時，加上購物車圖示縮小 20% 的反饋；這些在開發過程中不斷優化的互動效果，在最後整合到一起時，產生了驚艷的使用體驗。

- 將自己收藏的 46 部藍光電影製作成 JSON [API](https://github.com/rayc2045/horizontal-scrolling-theater/blob/master/src/assets/data/movie.json)，並透過 axios 非同步資料請求
- 使用基於 Webpack 的 [Vue CLI](https://cli.vuejs.org/) 做零配置原型建構
- 引入 [normalize.css](https://github.com/necolas/normalize.css/) 達到跨瀏覽器的樣式重置、使用預處理器 Sass 開發外觀，以及透過 [Scoped CSS](https://vue-loader.vuejs.org/guide/scoped-css.html#mixing-local-and-global-styles) 達到互不干擾的樣式封裝
- 外觀設計上
  - 載入網頁時加入水平捲動的動畫作為操作提示
  - 使用淺灰色作為電影卡片底色，持久凝視不眩光
  - 對電影標題、分類和敘述分別套用不同的文字大小、字重 (font weight) 和顏色，做出對比差異化
  - 在電影卡片封面外加上微陰影，並在鼠標碰觸卡片時，對卡片本身和卡片封面做出不同的上移距離，達到微 3D 效果
  - 加入電影到購物車後，對按鈕套用不同的內容和樣式，讓使用體驗更加直覺順暢
  - 使用 [ionicons](https://ionicons.com/) 的購物車 icon，並且在開、關購物車頁面時，切換線條、填充的版本
  - 開啟購物車時，虛化、暗化背景，添加層次和立體感
- 借助 [GSAP](https://greensock.com/gsap/) 之力
  - 加上綁定捲動事件和設定元素 `relative` 定位，透過改變 `left` 值實現橫向捲動功能
  - 透過點擊「加入購物車」按鈕後，取得當下電影封面位置和設計移動軌跡，達成漂亮的加入購物車動畫
  - 使用 Vue 的 `watch` API 監視購物車資料，從購物車新增或移除電影、導致資料更新時，觸發購物車 icon 縮小 20% 的互動效果
- 在加入購物車的動畫進行時，使用變數作為開關，阻擋期間的複數操作，確保 GSAP 互動效果始終如期運行
- 開啟購物車畫面而購物車為空，或是刪除電影導致購物車為空時，另外加上倒數計時器，1.6 秒後自動回到主畫面
- 使用 [Netlify](https://www.netlify.com/) 部署網站 👉 [Horizontal Scrolling Theater](https://vuejs-theater.netlify.app/)