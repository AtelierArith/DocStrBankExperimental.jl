```
  menu(fieldname::Union{Symbol,Nothing}, args...; content::Union{String,Vector} = "", kwargs...)
```

`menu`コンポーネントは、メニューを表示するための便利な方法です。ドロップダウンコンテンツとして`list`と非常に相性が良いですが、それに限られるわけではありません。   

---

### 例

---

### 表示

```julia-repl
julia> btn("基本メニュー", color="primary", [StippleUI.menu(nothing, [p("こんにちは")])])
```

---

### 引数

---

1. 動作

      * `target::Union{Bool, String}` - コンポーネントのトグルをトリガーするターゲット要素を設定します。'true'は親DOM要素を有効にし、'false'はDOM要素へのイベントの添付を無効にします。文字列（CSSセレクタ）またはDOM要素を使用すると、指定されたDOM要素（存在する場合）にイベントが添付されます。デフォルト値は`true`です。例：`target!=false` `target!=".my-parent"`
      * `noparentevent::Bool` - ターゲットDOM要素（要素を表示させるトリガー）へのイベントの添付をスキップします
      * `contextmenu::Bool` - コンポーネントがコンテキストメニューのように動作することを許可します。右クリック（またはモバイルでの長押し）で開きます
      * `scrolltarget::Union{String}` - 自動検出されたものの代わりにカスタムスクロールコンテナとして使用されるCSSセレクタまたはDOM要素。例：`scrolltarget=".scroll-target-class"` `scrolltarget="#scroll-target-id"` `scrolltarget="body"`
2. 位置

      * `fit::Bool` - メニューがターゲットの幅に少なくとも一致することを許可します
      * `cover::Bool` - メニューがターゲットを覆うことを許可します。使用すると、'self'および'fit'プロパティはもはや効果がありません
      * `anchor::String` - メニューの開始位置またはターゲットに対するアンカーポイントを設定する2つの値。例：`anchor="top left"` `anchor="bottom right"` `anchor="center"`
      * `self::String` - メニューの自身の位置をターゲットに対して設定する2つの値。例：`self="top left"` `self="bottom right"` `self="center"`
      * `offset::Vector` - メニューを水平方向および垂直方向にピクセル単位でオフセットするための2つの数の配列。例：`[8, 8]` `[5, 10]`
3. スタイル

      * `contentclass::Union{Vector, String, Dict}` - コンテンツに属性を付与するクラス定義。例：`my-special-class` `contentclass!="{ 'my-special-class': <condition> }"`
      * `contentstyle::Union{Vector, String, Dict}` - コンテンツに属性を付与するスタイル定義。例：`backgroundcolor: #ff0000` `contentstyle!="{ color: '#ff0000' }"`
      * `dark::Bool` - コンポーネントに背景が暗い色であることを通知します
      * `square::Bool` - コンテンツに四角いボーダーを強制します
      * `maxheight::String` - メニューの最大高さ。CSS単位でのサイズ、単位名を含む。例：`16px` `2rem`
      * `maxwidth::String` - メニューの最大幅。CSS単位でのサイズ、単位名を含む。例：`16px` `2rem`

```
