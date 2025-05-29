```
treat_all(ct::CausalTable)
```

`CausalTable`オブジェクトに介入し、すべての治療変数を0に設定します。

# 引数

  * `ct::CausalTable`: 単変量バイナリ治療を持つ`CausalTable`オブジェクト。

# 戻り値

`ct`の治療行列と同じヘッダーを持つ`NamedTuple`オブジェクトで、各治療変数は0に設定されています。

# 例

```@example
using Distributions
dgp = @dgp(
    L ~ Beta(2, 4),
    A ~ @.(Bernoulli(L)),
    Y ~ @.(Normal(A + L))
)
scm = StructuralCausalModel(dgp, :A, :Y, [:L])
data = rand(scm, 100)
treat_none(data)
```
