```
FinsDetails(;code="", date="")
```

[Financial Statements Details API](https://jpx.gitbook.io/j-quants-ja/api-reference/statements-1)

## Parameters

  * `code::AbstractString`: Stock code. (e.g. "8697")
  * `date::AbstractString`: Date. (e.g. "2018-01-01")

## Examples

```julia
julia> using JQuants

julia> fetch(FinsDetails(code="8697", date="2018-01-01"))
```
