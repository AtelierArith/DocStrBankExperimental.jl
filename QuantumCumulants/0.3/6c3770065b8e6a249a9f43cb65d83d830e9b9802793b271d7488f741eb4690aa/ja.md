```
to_numeric(q::QNumber, b::QuantumOpticsBase.Basis; level_map = nothing)
to_numeric(q::QNumber, state; level_map = nothing)
```

記号演算子 `q` を基底 `b` の同等の数値（行列）形式に変換します。オプションの引数 `level_map` は、[`Transition`](@ref) のレベルを `NLevelBasis` で与えられたものにマッピングする方法を指定する辞書に設定できます。**注意:** 遷移のレベルが記号的な場合、`level_map` を設定する必要があります。

参照: [`numeric_average`](@ref), [`initial_values`](@ref)

# 例

julia> to_numeric(Destroy(FockSpace(:fock), :a), FockBasis(10)) Operator(dim=11x11)   basis: Fock(cutoff=10)[...] ```
