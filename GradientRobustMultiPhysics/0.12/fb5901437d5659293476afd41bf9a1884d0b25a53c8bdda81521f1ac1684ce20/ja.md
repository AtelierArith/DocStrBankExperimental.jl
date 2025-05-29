```julia
add_unknown!(
    PDE::GradientRobustMultiPhysics.PDEDescription;
    equation_name,
    unknown_name,
    variables,
    algebraic_constraint
) -> Int64

```

PDEDescriptionに別の未知数を追加します。オプション引数 algebraic_constraint = true を指定すると、未知数と関連する方程式を代数制約としてマスクできます。（現在のところ、これはシステムがクランク・ニコルソンルールで時間的に統合される場合にのみ影響があります。）
