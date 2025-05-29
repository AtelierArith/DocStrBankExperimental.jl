```
mutual_information(
    priors :: AbstractVector,
    conditionals :: AbstractMatrix
) :: Float64
```

$$
p(x)
$$

と$p(y)$の重なりのエントロピー。相互情報量は、[`shannon_entropy`](@ref)と[`joint_entropy`](@ref)から直接計算されます：

$$
I(X : Y) = S(X) + S(Y) - S(X,Y)
$$
