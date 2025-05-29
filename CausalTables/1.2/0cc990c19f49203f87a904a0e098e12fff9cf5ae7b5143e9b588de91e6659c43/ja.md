```
ape(scm::StructuralCausalModel, intervention::Function; samples = 10^6)
```

与えられた構造的因果モデル（SCM）に対する平均政策効果を、その効率境界とともに近似します。これは修正された治療政策の因果効果としても知られ、モンテカルロサンプリングを使用して近似されます。`intervention`が部分的に滑らかで可逆でない限り、推定された統計量は因果解釈を持たない可能性があることに注意してください。詳細は[Haneuse and Rotnizky (2013)](https://pubmed.ncbi.nlm.nih.gov/23913589/)を参照してください。数学的には、これは次のように表されます。

$$
E(Y(d(a) - Y(a))
$$

ここで、$d(a)$は治療変数$A$に対する介入を表し、$Y(d(a))$は治療$d(a)$の下での反事実的$Y$を表し、$Y(a)$は自然に観察された治療の値の下での反事実的結果を表します。この統計量はモンテカルロサンプリングを使用して近似されます。

`intervention`関数を生成するための便利な関数には、治療変数に定数（または定数ベクトル）を加算または乗算する関数をそれぞれ構築する`additive_mtp`と`multiplicative_mtp`があります。また、自分自身の介入関数を実装することもできます。この関数は、`CausalTable`オブジェクトを入力として受け取り、介入に従って修正された各治療変数をインデックス付けするNamedTupleオブジェクトを返す必要があります。介入を構築するための便利な関数については、`cast_matrix_to_table_function`も参照してください。

# 引数

  * `scm::StructuralCausalModel`: データをシミュレートするためのSCM。
  * `intervention::Function`: SCMに適用する介入関数。
  * `samples`: モンテカルロ近似のために`scm`から引き出すサンプルの数（デフォルトは10^6）。これは近似の精度を制御します。

# 戻り値

次の内容を含む名前付きタプル：

  * `μ`: ATU近似。

# 例

```@example
using Distributions
dgp = CausalTables.@dgp(
    L ~ Beta(2, 4),
    A ~ @.(Normal(L)),
    Y ~ @.(Normal(A + 2 * L + 1))
)
scm = CausalTables.StructuralCausalModel(dgp, [:A], [:Y], [:L])
ape(scm, additive_mtp(0.5))
ape(scm, multiplicative_mtp(2.0))

# カスタム介入関数の例
custom_intervention = cast_matrix_to_table_function(x -> exp.(x))
ape(scm, custom_intervention)

```
