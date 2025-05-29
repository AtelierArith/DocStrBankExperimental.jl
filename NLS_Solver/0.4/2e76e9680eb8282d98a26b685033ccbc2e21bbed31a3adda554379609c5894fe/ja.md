```julia
create_NLS_problem_using_ForwardDiff(r::Function;domain_image_dim::Pair{Int,Int})
```

自動微分を使用して[`eval_r_J`](@ref)関数が自動的に定義される[`AbstractNLS`](@ref)の特化インスタンスを作成します。

  * `r`はパラメータベクトルθをその残差にマッピングする関数です。ヤコビ行列は`ForwardDiff`パッケージを使用して計算されます。
  * `domain_image_dim`は`θ length => r length`の形式のペアで、ドメインとコドメインの次元を定義します。

# 使用例

ロゼンブロック関数を定義する例

$$
\frac{1}{2}\|r(\theta)\|^2\text{ where }r = \sqrt{2} \left( \begin{array}{c}  1-\theta_1 \\ 10(\theta_2-\theta_1^2) \end{array} \right)
$$

```julia
nls = create_NLS_problem_using_ForwardDiff(2 => 2) do θ
     sqrt(2) sqrt(2)* [ 1-θ[1], 10*(θ[2]-θ[1]^2) ]* [ 1-θ[1], 10*(θ[2]-θ[1]^2) ]
end
```
