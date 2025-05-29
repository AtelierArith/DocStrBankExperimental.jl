```
att(scm::StructuralCausalModel; samples = 10^6)
```

与えられた構造的因果モデル（SCM）に対する処置を受けた者の平均処置効果（ATT）を、その効率境界と共に、単変量バイナリ処置について近似します。数学的には、これは次のように表されます。

$$
E(Y(1) - Y(0) \mid A = 1)
$$

ここで、$Y(a)$は、処置$A$が$a$に設定されていた場合の反実仮想的な$Y$を表します。この統計量は、モンテカルロサンプリングを使用して近似されます。

# 引数

  * `scm::StructuralCausalModel`: データをシミュレートするためのSCM。
  * `samples`: モンテカルロ近似のために`scm`から引き出すサンプルの数（デフォルトは10^6）。これは近似の精度を制御します。

# 戻り値

次の内容を含む名前付きタプル：

  * `μ`: ATTの近似値。
  * `eff_bound`: 反実仮想的な応答の分散で、IIDデータに対する効率境界に等しいです。観測が相関している場合、これは意味のある解釈を持たないかもしれません。

# 例

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
att(scm)
```
