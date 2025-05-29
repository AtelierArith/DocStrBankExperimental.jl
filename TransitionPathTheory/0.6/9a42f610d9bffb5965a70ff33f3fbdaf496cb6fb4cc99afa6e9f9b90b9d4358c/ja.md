```
nonstationary_statistics(tpt, horizon; B_to_S::Symbol = :interior, initial_dist = :stat)
```

次の統計量を `NamedTuple` で計算して返します：

  * `density`
  * `reactive_density`
  * `tAB_cdf`

### 引数

  * `tpt`: [`TPTProblem`](@ref)。
  * `horizon`: 計算を切り捨てる時間ステップ。`horizon` の値は、A から出た軌道がその時点までに B に到達することを強制するものではないことに注意してください。

### オプション引数

  * `initial_dist`: `𝒜` 内の初期分布がどのように計算されるかを決定する `Symbol`。

      * `:stat`: 初期分布は、制限された `𝒜` の `𝒫(tpt)` の定常分布に等しい。
      * `:uniform`: `𝒜` 上で支持される一様分布。
