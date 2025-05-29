```
log_header(colnames, coltypes)
```

`colnames`にある名前を使用して、`coltypes`に従ってフォーマットされたヘッダーを作成します。内部フォーマット仕様は`SolverCore.formats`によって提供され、デフォルトのヘッダー翻訳は`SolverCore.default_headers`によって提供されます。

入力:

  * `colnames::Vector{Symbol}`: 列名。
  * `coltypes::Vector{DataType}`: 列の型。

キーワード引数:

  * `hdr_override::Dict{Symbol,String}`: デフォルトのヘッダーを上書きします。
  * `colsep::Int`: 列間のスペースの数（デフォルト: 2）

関連項目 [`log_row`](@ref)。
