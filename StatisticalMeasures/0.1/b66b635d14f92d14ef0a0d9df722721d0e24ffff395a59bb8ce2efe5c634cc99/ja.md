```
measures(needle::Union{AbstractString,Regex}; trait_options...)
```

*実験的*であり、パッチリリース間での動作が壊れる可能性があります。

ドキュメント文字列に `needle` を含む測定値を見つけます。 そのような測定値のコンストラクタをキーとした辞書を返します。

```
julia> measures("Matthew")
LittleDict{Any, Any, Vector{Any}, Vector{Any}} with 1 entry:
  MatthewsCorrelation => (aliases = ("matthews_correlation", "mcc"), consumes_multiple_obse…
```
