```
function theme() :: String
```

Stippleアプリとページのテーマサポートを提供します。StippleのデフォルトCSSファイルが含まれており、HTMLタグの形で追加要素を`Stipple.Layout.THEMES[][]`コレクションにプッシュすることで注入できます。

### 例

```julia
julia> theme()
"<link href="https://fonts.googleapis.com/css?family=Material+Icons" rel="stylesheet" /><link href="https://fonts.googleapis.com/css2?family=Lato:ital,wght@0,400;0,700;0,900;1,400&display=swap" rel="stylesheet" /><link href="/css/stipple/stipplecore.css" rel="stylesheet" />"

julia> StippleUI.theme()
"<link href="/css/stipple/quasar.min.css" rel="stylesheet" />"

julia> push!(Stipple.Layout.THEMES[], StippleUI.theme)
```
