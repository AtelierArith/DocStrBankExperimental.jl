```
split_sums(term::SymbolicUtils.Symbolic,amount::Union{<:SymbolicUtils.Sym,<:Int64})
split_sums(me::MeanfieldEquations,amount)
```

関数は、与えられた項の内部の和を分割します。和は、`amount`引数で指定された数の等しい和に分割され、そのうちの1つの和のみがインデックスの依存関係（不等しいインデックス）を考慮します。

# 引数

*`me::MeanfieldEquations`: 評価される[`MeanfieldEquations`](@ref)エンティティで、任意の記号式でもかまいません。 *`amount::Union{<:SymbolicUtils.Sym,<:Int64}`: 和が分割される項の数を決定する数または記号
