```
weighted_iterator(d)
```

分布 `d` の値と確率のペアを通じてイテレータを返します。

これは値の反復を高速化するために設計されています。可能であれば、分布はカスタム最適化された実装を提供することが推奨されます。

# 例

```julia-repl
julia> d = BoolDistribution(0.7)
BoolDistribution(0.7)

julia> collect(weighted_iterator(d))
2-element Array{Pair{Bool,Float64},1}:
  true => 0.7
 false => 0.3
```
