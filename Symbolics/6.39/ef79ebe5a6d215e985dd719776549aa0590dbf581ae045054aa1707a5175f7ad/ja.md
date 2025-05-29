```julia
semipolynomial_form(
    expr,
    vars,
    degree::Real;
    consts
) -> Tuple{Any, Any}

```

2つのオブジェクトのタプルを返します：

1. 指定された `degree` までの `vars` の単項式によってキー付けされた係数の辞書、
2. 単項式と係数の積として表されないすべての項を持つ残差式

`degree` は非負の数である必要があります。

`consts` が `true` に設定されている場合、返される辞書にはキー `1` が含まれ、その対応する値は定数項になります。 `false` の場合、定数項は残差の一部になります。
