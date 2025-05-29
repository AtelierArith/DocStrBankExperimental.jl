```julia
struct NLS_ForwardDiff <: AbstractNLS
    ...
end

```

`ForwardDiff`パッケージを使用してヤコビ行列を計算する特化版です。

[`AbstractNLS`](@ref)と比較すると、次の関数を定義するだけです：

  * [`parameter_size`](@ref) : $n_θ$を返します
  * [`residue_size`](@ref) : $n_S$を返します
  * [`eval_r`](@ref) : $\mathbf{r}$の計算

参照: [`create_NLS_problem_using_ForwardDiff`](@ref) 
