```
function stylesheet(href::String; args...) :: String
```

指定された `href` のCSSスタイルシートを参照するHTML `link` タグを生成します。

### 例

```julia
julia> stylesheet("https://fonts.googleapis.com/css?family=Material+Icons")
"<link href="https://fonts.googleapis.com/css?family=Material+Icons" rel="stylesheet" />"
```
