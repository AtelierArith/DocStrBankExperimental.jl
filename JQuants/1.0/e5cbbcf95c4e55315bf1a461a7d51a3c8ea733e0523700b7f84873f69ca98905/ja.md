```
FinsDetails(;code="", date="")
```

[Financial Statements Details API](https://jpx.gitbook.io/j-quants-ja/api-reference/statements-1)

## パラメータ

  * `code::AbstractString`: 株式コード。 (例: "8697")
  * `date::AbstractString`: 日付。 (例: "2018-01-01")

## 例

```julia
julia> using JQuants

julia> fetch(FinsDetails(code="8697", date="2018-01-01"))
```
