```
icon(name::Union{String,Symbol}, args...; content::Union{String,Vector,Function} = "", kwargs...)
```

Stippleは、[Material Icons](https://fonts.google.com/icons?selected=Material+Icons)、[Font Awesome](https://fontawesome.com/icons)、[Ionicons](https://ionic.io/ionicons)、[MDI](https://materialdesignicons.com/)、[Eva Icons](https://akveo.github.io/eva-icons/#/)、[Themify Icons](https://themify.me/themify-icons)、[Line Awesome](https://icons8.com/line-awesome)、および[Bootstrap Icons](https://icons.getbootstrap.com/)を標準でサポートしています。

さらに、任意のアイコンライブラリのサポートを[自分で追加することができます](https://v1.quasar.dev/vue-components/icon#custom-mapping)。

---

### 例

---

### 表示

```julia-repl
julia> icon("font_download", class="text-primary", style="font-size: 32px;")
julia> icon("warning", class="text-red", style="font-size:4rem;")
julia> icon("format_size", style="color: #ccc; font-size: 1.4em;")
julia> icon("print", class="text-teal", style="font-size: 4.4em;")
julia> icon("today", class="text-orange", style="font-size: 2em;")
julia> icon("style", style="font-size: 3em;")
```

---

### 引数

---

1. コンテンツ

      * `tag::String` - レンダリングするHTMLタグ。アイコンが供給されていない場合やsvgアイコンの場合を除く。例: `div` `i`
      * `left::Bool` - アイコンが何かの左側にある場合に便利: アイコンの右側に標準のマージンを適用します。
      * `right::Bool` - アイコンが何かの右側にある場合に便利: アイコンの左側に標準のマージンを適用します。
2. モデル

      * `name::String` - アイコン名; 'img:'プレフィックスを使用していない限り、アイコンライブラリがインストールされていることを確認してください; 値として'none'（String）が使用されると、アイコンはレンダリングされません（ただし、画面の実際のスペースは依然として使用されます）。例: `map` `ion-add` `img:https://cdn.quasar.dev/logo/svg/quasar-logo.svg` `img:path/to/some_image.png`
3. スタイル

      * `size::String` - CSS単位でのサイズ、単位名または標準サイズ名を含む。例: `16px` `2rem` `xs` `md`
      * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette)からのコンポーネントの色名。例: `primary` `teal-10`
