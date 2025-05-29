```
  imageview(args...; kwargs...)
```

`imageview`コンポーネントは、画像（任意の画像形式）を簡単に扱えるようにし、さらに多くの機能（例：アスペクト比を設定する機能）とともに、素敵なローディング効果を追加します。

---

### 例

---

### モデル

```julia-repl
julia> @vars Model begin
          url::R{String} = "https://placeimg.com/500/300/nature"
       end
```

### ビュー

```julia-repl
julia> imageview(src = :url, spinnercolor = "white", style = "height: 140px; max-width: 150px" )
julia> imageview(src = :url, style = "height: 140px; max-width: 150px", [
          template("", "v-slot:loading", [spinner(:gears, color = "white", wrap = StippleUI.NO_WRAPPER)]),
       ])
```

---

### 引数

---

1. 挙動     * `transition::String` - [埋め込みトランジション](https://v1.quasar.dev/options/transitions)の1つ ex. `fade` `slide-down`     * `nativecontextmenu::Bool` - 画像のネイティブコンテキストメニューを有効にする
2. コンテンツ     * `ratio::Union{String, Int}` - コンポーネントがアスペクト比を維持するよう強制する ex. `ratio!="4/3"` `(数値形式) ratio!="16/9"` `(文字列形式) ratio="1"`     * `alt::String` - 画像が表示できない場合の代替テキストを指定する ex. `二匹の猫`     * `no__transition::Bool` - トランジションを使用しない; より速いレンダリング     * `contain::Bool` - 画像が表示される際に、画像の横または縦に追加の空白が必要かどうかに関わらず、完全に収まるようにする
3. モデル     * `src::String` - 画像へのパス ex. `(公開フォルダ) src="img/something.png"` `(アセットフォルダ) src="~assets/my-img.gif"` `(URL) src="https://placeimg.com/500/300/nature"`     * `srcset::String` - <img> srcset属性と同じ構文。 ex. `elva-fairy-320w.jpg 320w, elva-fairy-480w.jpg 480w`     * `sizes::String` - <img> sizes属性と同じ構文。 ex. `(max-width: 320px) 280px, (max-width: 480px) 440px, 800px`     * `width::String` - 画像の幅を強制する; 単位（pxまたは%）を含める必要がある ex. `280px` `70%`     * `height::String` - 画像の高さを強制する; 単位（pxまたは%）を含める必要がある ex. `280px` `70%`     * `placeholdersrc::String` - 画像の読み込みを待っている間に、プレースホルダー画像を使用することができる ex. `(公開フォルダ) src="img/something.png"` `(アセットフォルダ) src="~assets/my-img.gif"` `(URL) src="https://placeimg.com/500/300/nature"`
4. スタイル

      * `color::String` - [カラーパレット](https://quasar.dev/style/color-palette)からのコンポーネントの色名 eg. `primary` `teal-10`
      * `imgclass::Union{Vector, String, Dict}` - 画像のコンテナに属性を付与するクラス定義; キャプションには適用されない ex. `my-special-class` `imgclass!="{ 'my-special-class': <condition> }"`
      * `imgstyle::Dict` - 画像のコンテナにCSSを適用する; キャプションには適用されない ex. `imgstyle!="{ transform: 'rotate(45deg)' }"`
      * `spinnercolor::String` - デフォルトのスピナーの色名（'loading'スロットを使用しない場合） `primary` `teal-10`
      * `spinnersize::String` - デフォルトのスピナーのサイズ（'loading'スロットを使用しない場合）に対するCSS単位でのサイズ、単位名を含む ex. `16px` `2rem`
