```
XPRSnlpgetformula(prob, row, parsed, maxtypes, type, value)::ntypes, type, value
```

トークンに分割された式として単一の行列式を取得します。

# 引数

  * `prob::XPRSprob`: 現在のSLP問題。
  * `row::Integer`: 式の行インデックスを保持する整数。
  * `parsed::Integer`: 行の式を内部の未解析形式（`parsed`=0）または解析済み（逆ポーランド）形式（`parsed`=1）で返すかどうかを示す整数。
  * `maxtypes::Integer`: 戻すトークンの最大数、すなわち、タイプと値の配列の長さ。
  * `type::Union{XPRSallocatable,Nothing,AbstractVector{Int32}}`: 式のトークンタイプを保持する整数配列。この引数に`XPRS_ALLOC`を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すと、その情報を照会しません。
  * `value::Union{XPRSallocatable,Nothing,AbstractVector{Float64}}`: `type`に対応する値のダブル配列。この引数に`XPRS_ALLOC`を渡すと、関数が適切なサイズの配列を自動的に割り当てます。この引数に`nothing`を渡すと、その情報を照会しません。

# 戻り値

  * `ntypes::Int32`: `XSLP_EOF`トークンを含む式の長さに設定されます。
  * `type::Union{Nothing,AbstractVector{Int32}}`: 式のトークンタイプを保持する整数配列。
  * `value::Union{Nothing,AbstractVector{Float64}}`: `type`に対応する値のダブル配列。

C APIの対応する関数[XPRSnlpgetformula](https://www.fico.com/fico-xpress-optimization/docs/latest/solver/optimizer/HTML/XPRSnlpgetformula.html)のドキュメントも参照してください。
