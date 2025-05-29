```
tdvp(operator, t::Number, init::MPS; time_step, nsteps, kwargs...)
```

時間依存変分原理 (TDVP) アルゴリズムを使用して `exp(t * operator) * init` を計算します。これは、MPS テンソルの交互最適化と `operator` の局所 Krylov 指数化に基づく効率的なアルゴリズムです。

`time_step` または `nsteps` のいずれかを指定してください。両方が指定されている場合、`time_step * nsteps == t` を満たす必要があります。どちらも指定されていない場合、デフォルトは `nsteps=1` であり、これは `time_step == t` を意味します。

返されるもの:

  * `state::MPS` - 時間発展した MPS

```
