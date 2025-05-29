```julia
semipolynomial_form(
    exprs::AbstractArray,
    vars,
    degree::Real;
    consts
) -> Tuple{Any, Any}

```

`exprs` の各式に対して半多項式形式を計算し、係数辞書のベクトルと残差項のベクトルという2つのオブジェクトのタプルを返します。

`consts` が `true` に設定されている場合、返される辞書にはキー `1` が含まれ、その対応する値は定数項になります。`false` の場合、定数項は残差の一部になります。
