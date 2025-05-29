```
cumulant_expansion(avg, order::Int)
```

演算子の[`average`](@ref)のために、共分散を無視して、モーメントの観点から`order`まで展開します。

詳細は、https://en.wikipedia.org/wiki/Cumulant#Joint_cumulants を参照してください。

# 例

```
julia> avg = average(a*b)
⟨a*b⟩

julia> cumulant_expansion(avg,1)
(⟨a⟩*⟨b⟩)

julia> avg = average(a*b*c)
⟨a*b*c⟩

julia> cumulant_expansion(avg,2)
((⟨a*b⟩*⟨c⟩)+(⟨a*c⟩*⟨b⟩)+(⟨a⟩*⟨b*c⟩)+(-2*⟨a⟩*⟨b⟩*⟨c⟩))
```

# オプション引数

*simplify=true: 結果を簡略化するかどうかを指定します。 *kwargs...: 簡略化に渡されるさらなるキーワード引数。
