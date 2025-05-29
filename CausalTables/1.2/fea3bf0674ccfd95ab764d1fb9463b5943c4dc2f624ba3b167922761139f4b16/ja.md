```
intervene(ct::CausalTable, intervention::Function)
```

CausalTable内の治療ベクトルに`intervention`を適用し、介入された治療を持つ新しいCausalTableを出力します。

# 引数

  * `ct::CausalTable`: 介入すべき治療に関するデータ
  * `intervention::Function`: 親変数に適用される介入を定義する関数。治療ベクトルまたは行列に作用する関数をCausalTableに作用する関数に変換するには、`cast_matrix_to_table_function`を使用します。

# 戻り値

`ct`と同じデータを含む`CausalTable`ですが、`intervention`に従って治療変数が修正されています。

# 例

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
ct = rand(scm, 100)
intervene(ct, treat_all)
```
