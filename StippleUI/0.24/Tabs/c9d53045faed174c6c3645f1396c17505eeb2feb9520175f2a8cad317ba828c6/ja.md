```
  tabgroup(fieldname::Union{Symbol,Nothing} = nothing, args...; kwargs...)
```

## `menu` コンポーネントは、メニューを表示するための便利な方法です。ドロップダウンコンテンツとして `list` と非常に相性が良いですが、それに限られるわけではありません。

### 例

---

### モデル

```julia-repl
julia> @vars TabModel begin
          tab_m::R{String} = "tab"
       end
```

### ビュー

```julia-repl
julia> tabgroup(:tab_m, inlinelabel=true, class="bg-primary text-white shadow-2", [
          tab(name="photos", icon="photos", label="Photos"),
          tab(name="videos", icon="slow_motion_video", label="Videos"),
          tab(name="movies", icon="movie", label="Movies")
       ])
```

---

### 引数

---

1. 挙動

      * `target::Union{Bool, String}` - タブコンテナの幅のブレークポイント（ピクセル単位）で、タブが自動的に整列します。デフォルト: `600` | 例: `breakpoint! ="500"`
2. コンテンツ

      * `vertical::Bool` - 垂直デザインを使用する（タブが横に並ぶのではなく、上下に重なる）
      * `outsidearrows::Bool` - タブの両側に矢印を配置するためのスペースを確保する（矢印は非アクティブ時にフェードアウトする）
      * `mobilearrows::Bool` - モバイルで矢印を強制的に表示する（必要な場合）
      * `align::String` - タブコンテナ内のタブの水平方向の整列。デフォルト: `center` | 受け入れられる値: `left`, `center`, `right`, `justify` | 例: `right`
      * `breakpoint::Union{Int, String}` - タブコンテナの幅のブレークポイント（ピクセル単位）で、タブが自動的に整列します。デフォルト: `600` | 例: `breakpoint! = "500"`
      * `lefticon::String` - タブがタブコンテナの幅を超えたときに、左にスクロールするために使用されるデフォルトの矢印を置き換えるアイコンの名前。例: `arrow_left`
      * `righticon::String` - タブがタブコンテナの幅を超えたときに、右にスクロールするために使用されるデフォルトの矢印を置き換えるアイコンの名前。例: `arrow_right`
      * `stretch::Bool` - フレックスボックスの親で使用されると、タブは親の高さに合わせて伸びます
      * `shrink::Bool` - デフォルトでは、`tabs` は利用可能なスペースに合わせて成長するように設定されていますが、このプロパティを使用するとそれを逆転させることができます; コンポーネントを `toolbar` に配置する際に便利（かつ必要）
      * `switchindicator::Bool` - インジケーターの位置を切り替えます（垂直モードではタブの左側、デフォルトの水平モードではタブの上）
      * `narrowindicator::Bool` - インジケーターがタブのコンテンツ（テキストまたはアイコン）と同じ幅になることを許可します（タブ全体の幅ではなく）
      * `inlinelabel::Bool` - アイコンが使用される場合、テキストをアイコンとインラインにすることを許可します
      * `nocaps::Bool` - タブ内のすべての文字を大文字にするのをオフにします（これがデフォルトです）
3. スタイル

      * `activeclass::String` - アクティブなタブに設定されるクラス
      * `activecolor::String` - アクティブなタブのテキストに割り当てられる色。例: `teal-10` `primary`
      * `activecolorbg::String` - アクティブなタブの背景に割り当てられる色。例: `teal-10` `primary`
      * `indicatorcolor::String` - アクティブなタブのインジケーター（下線）に割り当てられる色。例: `teal-10` `primary`
      * `contentclass::String` - コンテンツラッパーに割り当てられるクラス定義
      * `dense::Bool` - 密なモード; より少ないスペースを占有します

```
