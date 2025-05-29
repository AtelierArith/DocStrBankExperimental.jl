```
function layout(output::Union{String,Vector}; partial::Bool = false, title::String = "", class::String = "", style::String = "",
                  head_content::String = "", channel::String = Genie.config.webchannels_default_route) :: String
```

基本的なウェブページ構造を作成するためのユーティリティで、doctypeや<HTML>、<HEAD>、<TITLE>、<META viewport>、および<BODY>タグを含み、出力コンテンツと共に提供されます。

`partial`が`true`の場合、ページレイアウトのHTML要素は返されません。

### 例

```julia
julia> layout([
        span("Hello", @text(:greeting))
        ])
"<!DOCTYPE html>
<html><head><title></title><meta name="viewport" content="width=device-width, initial-scale=1, maximum-scale=1, user-scalable=no, minimal-ui" /></head><body class style><link href="https://fonts.googleapis.com/css?family=Material+Icons" rel="stylesheet" /><link href="https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;0,900;1,400&display=swap" rel="stylesheet" /><link href="/css/stipple/stipplecore.css" rel="stylesheet" /><link href="/css/stipple/quasar.min.css" rel="stylesheet" /><span v-text='greeting'>Hello</span><script src="/js/channels.js?v=1.17.1"></script><script src="/js/underscore-min.js"></script><script src="/js/vue.global.prod.js"></script><script src="/js/quasar.umd.prod.js"></script>
<script src="/js/apexcharts.min.js"></script><script src="/js/vue-apexcharts.min.js"></script><script src="/js/stipplecore.js" defer></script><script src="/js/vue_filters.js" defer></script></body></html>"
```

```julia
julia> layout([
        span("Hello", @text(:greeting))
        ], partial = true)
"<link href="https://fonts.googleapis.com/css?family=Material+Icons" rel="stylesheet" /><link href="https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;0,900;1,400&display=swap" rel="stylesheet" /><link href="/css/stipple/stipplecore.css" rel="stylesheet" /><link href="/css/stipple/quasar.min.css" rel="stylesheet" /><span v-text='greeting'>Hello</span><script src="/js/channels.js?v=1.17.1"></script><script src="/js/underscore-min.js"></script><script src="/js/vue.global.prod.js"></script><script src="/js/quasar.umd.prod.js"></script>
<script src="/js/apexcharts.min.js"></script><script src="/js/vue-apexcharts.min.js"></script><script src="/js/stipplecore.js" defer></script><script src="/js/vue_filters.js" defer></script>"
```
