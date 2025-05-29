```
Epoch(str[, format])
```

文字列 `str` から `Epoch` を構築します。オプションで、[`DateFormat`](https://docs.julialang.org/en/stable/stdlib/Dates/#Dates.DateFormat) オブジェクトまたは文字列として `format` 定義を渡すことができます。`DateFormat` がサポートする文字コードに加えて、`D` という文字コードがサポートされており、これは「年の日」として解析されます（以下の例を参照）。また、時間スケールとして解析される `t` という文字コードもサポートされています。デフォルトのフォーマットは `yyyy-mm-ddTHH:MM:SS.sss ttt` です。

**注意:** このコンストラクタは、`str` の一部に時間スケールが含まれている必要があることに注意してください。例えば、`2018-02-06T00:00 TAI` のように。そうでない場合は、明示的なコンストラクタを使用してください。例えば、`Epoch{TAI}` のように。

### 例

```jldoctest; setup = :(using AstroTime)
julia> Epoch("2018-02-06T20:45:00.0 TAI")
2018-02-06T20:45:00.000 TAI

julia> Epoch("2018-037T00:00 TAI", "yyyy-DDDTHH:MM ttt")
2018-02-06T00:00:00.000 TAI
```
