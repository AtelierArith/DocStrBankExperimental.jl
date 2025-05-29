```
tooltip(fieldname::Symbol, args...; kwargs...)
```

`tooltip`コンポーネントは、アプリ内の特定の領域についてユーザーに追加情報を提供したいときに使用します。ターゲット要素の上にマウスをホバーさせる（またはモバイルプラットフォームで素早くタップする）と、ツールチップが表示されます。

---

### 例

---

### 表示

```julia-repl
julia> btn("Hover me", color="primary", [
          tooltip("Some text as content of Tooltip")
       ])
julia> Html.div(class="inline bg-amber rounded-borders cursor-pointer", style="max-width: 300px", [
          Html.div(class="fit flex flex-center text-center non-selectable q-pa-md", "I am groot!<br>(Hover me!)", [
            tooltip("I am groot!")
       ])
julia> 
])
```

---

### 引数

---

1. 挙動

      * `transitionshow::String` - 内蔵の[トランジション](https://v1.quasar.dev/options/transitions)をサポートします。例：`fade` `slide-down`
      * `transitionhide::String` - 内蔵の[トランジション](https://v1.quasar.dev/options/transitions)をサポートします。例：`fade` `slide-down`
      * `scrolltarget::String` - 自動検出されたものの代わりにカスタムスクロールコンテナとして使用されるCSSセレクタまたはDOM要素。例：`scrolltarget=".scroll-target-class"` `scrolltarget="#scroll-target-id"` `scrolltarget="body"`
      * `target::Union{String, Bool}` - ツールチップのトグルをトリガーするターゲット要素を設定します。'true'は親DOM要素を有効にし、'false'は任意のDOM要素へのイベントの添付を無効にします。文字列（CSSセレクタ）を使用すると、指定されたDOM要素（存在する場合）にイベントが添付されます。例：`target=".my-parent"` `target!=false`
      * `noparentevent::Bool` - ターゲットDOM要素（要素を表示させるトリガー）へのイベントの添付をスキップします。
      * `delay::Int` - ツールチップが遅延して表示されるように設定します。デフォルト値：`0` 例：`delay!="500"`
      * `hidedelay::Int` - ツールチップが遅延して消えるように設定します。デフォルト値：`0` 例：`hidedelay!="600"`
2. コンテンツ

      * `maxheight::String` - ツールチップの最大高さ。CSS単位でのサイズ、単位名を含む。例：`16px` `2rem`
      * `maxwidth::String` - ツールチップの最大幅。CSS単位でのサイズ、単位名を含む。例：`16px` `2rem`
3. 位置

      * `anchor::String` - ツールチップのターゲットに対する開始位置またはアンカーポイントを設定する2つの値。例：`top left` `top middle` `top right` `top start` `top end` `center left` `center middle` `center right` `center start` `center end` `bottom left` `bottom middle` `bottom right` `bottom start` `bottom end`
      * `self::String` - ツールチップのターゲットに対する自身の位置を設定する2つの値。例：`top left` `top middle` `top right` `top start` `top end` `center left` `center middle` `center right` `center start` `center end` `bottom left` `bottom middle` `bottom right` `bottom start` `bottom end`
      * `offset::Vector` - ツールチップを水平方向および垂直方向にピクセル単位でオフセットするための2つの数値の配列。デフォルト値：`[14,14]` 例：`[5, 10]`
4. スタイル

      * `contentclass::Union{Vector, String, Dict}` - コンテンツに割り当てるクラス定義。例：`my-special-class` `contentclass!="{ 'my-special-class': <condition> }"`
      * `contentstyle::Union{Vector, String, Dict}` - コンテンツに割り当てるスタイル定義。例：`background-color: #ff0000` `contentstyle!="{ color: '#ff0000' }"`
