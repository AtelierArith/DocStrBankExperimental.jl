```
ate(scm::StructuralCausalModel; samples = 10^6)
```

与えられた構造的因果モデル（SCM）に対する平均処置効果（ATE）を、その効率境界と共に近似します。これは単変量バイナリ処置に対して次のように表されます。

$$
E(Y(1) - Y(0))
$$

ここで、$Y(a)$は処置$A$が$a$に設定されていた場合の反事実的$Y$を表します。この統計量はモンテカルロサンプリングを用いて近似されます。

# 引数

  * `scm::StructuralCausalModel`: データをシミュレートするためのSCM。
  * `samples`: モンテカルロ近似のために`scm`から引き出すサンプルの数（デフォルトは10^6）。これは近似の精度を制御します。

# 戻り値

次の内容を含む名前付きタプル：

  * `μ`: ATEの近似値。
  * `eff_bound`: 反事実的応答の分散で、IIDデータに対する効率境界に等しいです。観測が相関している場合、これは意味のある解釈を持たないかもしれません。

# 例

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
ate(scm)
```
