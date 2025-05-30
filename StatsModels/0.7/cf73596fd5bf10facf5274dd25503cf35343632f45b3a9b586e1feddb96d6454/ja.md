```
InterceptTerm{HasIntercept} <: AbstractTerm
```

回帰モデルにおける「切片」項の存在または（明示的な）不在を表します。これらの項は、`apply_schema(::ConstantTerm, schema, ::Type{<:StatisticalModel})`によって式の中の[`ConstantTerm`](@ref)sから生成されます。`1`は`InterceptTerm{true}`を生成し、`0`または`-1`は`InterceptTerm{false}`を生成します（これは、[`implicit_intercept`](@ref)特性によって明示的に切片を省略するモデルに対して切片を含むことを示します）。
