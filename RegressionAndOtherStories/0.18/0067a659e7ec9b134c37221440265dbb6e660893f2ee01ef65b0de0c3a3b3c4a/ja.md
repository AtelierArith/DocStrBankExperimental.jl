トランクプロットを作成します。

```julia
trankplot()

```

## 位置引数

```julia
* `df::DataFrame` # ドローを保持するDataFrame
* `param::AbstractString` # 使用するシンボル
```

## キーワード引数

```julia
* `bins = 40` # ビンの数
* `n_draws = 1000` # df内のドローの数
* `n_chains = 4` # dfに追加されたチェーンの数
* `n_eff = 0` # 有効なサンプル数
```
