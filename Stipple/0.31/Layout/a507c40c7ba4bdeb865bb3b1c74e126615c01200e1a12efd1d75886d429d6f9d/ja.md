```
function cell(args...; size::Int=0, xs::Int=0, sm::Int=0, md::Int=0, lg::Int=0, xl::Int=0, kwargs...)
```

QuasarのフレックスグリッドCSSクラス`col`を持つ`div` HTML要素を作成します。さらに、セルはStippleテーマによって制御されるクラス`st-col`を持ちます。

サイズが指定されている場合、クラス`col-$size`が代わりに追加されます。

タグクラス（`xs`、`sm`、`md`、`lg`、`xl`）が指定されている場合、それぞれのクラス`col-$tag-$md`が追加されます。例えば、`col-sm-6`のようになります。

パラメータ：

  * `""` / `0`: 共有の残りのスペース（例：`"col"`、`"col-sm"`）
  * `1` - `12` / `"1"` - `"12"`: 列の幅（例：`"col-5"`、`"col-sm-5"`）
  * `"auto"`/`:auto`: コンテンツからの高さ/幅（`"col-auto"`、`"col-sm-auto"`）
  * `-1` / `nothing`: 指定なし

セルは通常、[`row`](@ref)sまたは[`column`](@ref)sの中に含まれます。詳細については[Quasarのフレックスグリッド](https://quasar.dev/layout/grid/introduction-to-flexbox)を参照してください。

### 例

```julia
julia> row(cell(size = 2, md = 6, sm = 12, span("Hello")))
"<div class="row"><div class="st-col col-2 col-sm-12 col-md-6"><span>Hello</span></div></div>"
```
