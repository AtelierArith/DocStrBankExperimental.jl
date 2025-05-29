```
joint_entropy(priors :: AbstractVector, conditionals :: AbstractMatrix) :: Float64
```

確率密度関数 $P(x,y)$ の和のエントロピーを返します。結合エントロピーは、結合確率分布の [`shannon_entropy`](@ref) です：

$$
S(X,Y) = - \sum_{x,y} p(x,y) \log_2(p(x,y))
$$
