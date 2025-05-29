```
ApproximateJacobianSparsity(; ntrials = 5, rng = Random.default_rng(),
    epsilon = nothing, alg = GreedyD1Color())
```

`ntrials` のランダムベクトルを使用してヤコビ行列のスパースパターンを計算します。これは近似的な方法であり、スパースパターンは正確でない場合があります。

## キーワード引数

```
- `ntrials`: スパースパターンを計算するために使用するランダムベクトルの数
- `rng`: ランダムベクトルを生成するために使用される乱数生成器
- `alg`: 行列の色を計算するために使用されるアルゴリズム
- `epsilon`: 有限差分に基づくヤコビ行列近似のために、`epsilon` より小さい任意の数はゼロと見なされます。`nothing` が指定された場合、この値は `100 * eps(eltype(x))` として計算されます
```
