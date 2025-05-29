```
ReservoirSimResult(model, result::Jutul.SimResult, forces, extra = Dict(); kwarg...)
```

特定の貯水池シミュレーション結果を作成します。これには井戸曲線、貯水池の状態などが含まれます。これは `simulate_reservoir` からの戻り値の型です。

`ReservoirSimResult` は井戸の解、貯水池の状態、報告時間に展開できます：

```julia
res_result::ReservoirSimResult
ws, states, t = res_result
```

# フィールド

  * `wells`
  * `states`
  * `time`
  * `result`
  * `extra`

```
