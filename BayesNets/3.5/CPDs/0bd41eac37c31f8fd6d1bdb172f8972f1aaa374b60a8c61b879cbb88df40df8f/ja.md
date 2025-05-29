条件付き線形ガウスCPDは、常にNormal{Float64}を返します。

```
これは、CategoricalCPDとLinearGaussianCPDの組み合わせです。
N個の離散親とM個の連続親を持つ変数に対して、各離散インスタンス化に対してM個の親すべての線形ガウス分布を構築します。

                  { Normal(μ=a₁×continuous_parents(x) + b₁, σ₁) 離散インスタンス化1の場合
P(x|parents(x)) = { Normal(μ=a₂×continuous_parents(x) + b₂, σ₂) 離散インスタンス化2の場合
                  { ...
```
