```julia
IRKC(; eigen_est = nothing)
```

安定化された暗黙のルンゲクッタ法。暗黙のルンゲ-クッタ-チェビシェフ法。

### キーワード引数

  * `eigen_est`: 形式 `(integrator) -> integrator.eigen_est = upper_bound` の関数で、ここで `upper_bound` はヤコビ行列のスペクトル半径の推定上限です。 `eigen_est` が提供されない場合、`upper_bound` はべき反復を使用して推定されます。

## 参考文献

REF TBD
