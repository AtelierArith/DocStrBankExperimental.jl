```
cfdiff(scm::StructuralCausalModel, intervention1::Function, intervention2::Function; samples = 10^6)
```

2つの反実仮想応答平均の差を近似します。これは、治療に対して `intervention1` が適用された場合と `intervention2` が適用された場合のもので、与えられた構造的因果モデル（SCM）に基づいています。また、その効率境界も含まれます。数学的には、これは次のように表されます。

$$
E(Y(d_1(a)) - Y(d_2(a)))
$$

ここで、$d_1$ と $d_2$ は治療変数 $A$ に対して `intervention1` と `intervention2` が適用されることを表します。この統計量はモンテカルロサンプリングを使用して近似されます。

# 引数

  * `scm::StructuralCausalModel`: データをシミュレートするためのSCM。
  * `intervention1::Function`: 対比される最初の介入関数。
  * `intervention2::Function`: 対比される2番目の介入関数。
  * `samples`: モンテカルロ近似のために `scm` から引き出すサンプルの数（デフォルトは10^6）。これは近似の精度を制御します。

# 戻り値

次の内容を含む名前付きタプル：

  * `μ`: 反実仮想結果の平均差。

# 例

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
cfdiff(scm, treat_all, treat_none)
```
