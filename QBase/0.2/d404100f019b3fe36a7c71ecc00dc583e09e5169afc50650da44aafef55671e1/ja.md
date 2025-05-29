```
von_neumann_entropy( ρ :: AbstractMatrix ) :: Float64
```

密度行列のフォン・ノイマンエントロピー：

$$
S(\rho) = - \sum_j  \lambda_j \log_2(\lambda_j)
$$

ここで、$\lambda_j$ は量子状態 $\rho$ の固有値です。

`ρ` が [`is_density_matrix`](@ref) を満たさない場合、`DomainError` がスローされます。
