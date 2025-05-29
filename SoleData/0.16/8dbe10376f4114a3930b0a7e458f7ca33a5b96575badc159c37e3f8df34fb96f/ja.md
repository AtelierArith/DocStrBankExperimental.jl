```
PropositionalLogiset(table) <: AbstractPropositionalLogiset
```

命題解釈のログセットで、[Tables](https://github.com/JuliaData/Tables.jl)の実数/文字列/カテゴリ値のテーブルをラップしています。

# 例

この構造は命題式をチェックするために使用できます：

```julia
using SoleData, MLJBase

X = PropositionalLogiset(MLJBase.load_iris())

φ = parseformula(
    "sepal_length > 5.8 ∧ sepal_width < 3.0 ∨ target == "setosa"";
    atom_parser = a->Atom(parsecondition(SoleData.ScalarCondition, a; featuretype = SoleData.VariableValue))
)

check(φ, X, 10) # 単一のインスタンスで式をチェック

satmask = check(φ, X) # データセット全体で式をチェック

slicedataset(X, satmask)
slicedataset(X, (!).(satmask))
```

[`AbstractLogiset`](@ref)や[`AbstractAssignment`](@ref)も参照してください。
