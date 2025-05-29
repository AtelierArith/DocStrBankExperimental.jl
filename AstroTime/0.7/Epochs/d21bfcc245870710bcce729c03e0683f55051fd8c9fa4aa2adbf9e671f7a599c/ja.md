```
TTEpoch(str[, format])
```

文字列 `str` から TTEpoch を構築します。オプションで、[`DateFormat`](https://docs.julialang.org/en/stable/stdlib/Dates/#Dates.DateFormat) オブジェクトまたは文字列として `format` 定義を渡すことができます。`DateFormat` によってサポートされる文字コードに加えて、`D` コードがサポートされており、これは「年の日」として解析されます（以下の例を参照）。デフォルトのフォーマットは `yyyy-mm-ddTHH:MM:SS.sss` です。

### 例

```jldoctest; setup = :(using AstroTime)
julia> TTEpoch("2018-02-06T20:45:00.0")
2018-02-06T20:45:00.000 TT

julia> TTEpoch("February 6, 2018", "U d, y")
2018-02-06T00:00:00.000 TT

julia> TTEpoch("2018-37T00:00", "yyyy-DDDTHH:MM")
2018-02-06T00:00:00.000 TT
```
