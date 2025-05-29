```
cfmean(scm::StructuralCausalModel, intervention::Function; samples = 10^6)
```

`intervention`が処置に適用された場合の反実的平均を、与えられた構造的因果モデル（SCM）に対して、その効率境界と共に近似します。数学的には、この推定量は

$$
E(Y(d(a)))
$$

であり、ここで$d(a)$は処置変数$A$に対する介入を表します。この統計量はモンテカルロサンプリングを用いて近似されます。

# 引数

  * `scm::StructuralCausalModel`: データをシミュレートするためのSCM。
  * `intervention::Function`: SCMに適用する介入関数。
  * `samples`: モンテカルロ近似のために`scm`から引き出すサンプルの数（デフォルトは10^6）。これは近似の精度を制御します。

# 戻り値

以下を含む名前付きタプル：

  * `μ`: 反実的結果の平均。

# 例

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
cfmean(scm, treat_all)
cfmean(scm, treat_none)
```
