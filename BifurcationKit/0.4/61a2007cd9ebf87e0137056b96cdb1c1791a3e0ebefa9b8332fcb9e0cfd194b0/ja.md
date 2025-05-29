```julia
struct AutoSwitch{Talg, T} <: BifurcationKit.AbstractContinuationAlgorithm
```

自然連続が破棄されるときに、継続されるブランチの剛性に応じて自然連続とPALCの間を自動的に切り替える継続アルゴリズムです。

  * `alg::Any`: 自然連続が破棄されたときに切り替える継続アルゴリズム。通常は `PALC()`
  * `tol_param::Any`: PALC()に切り替えるための許容誤差、デフォルト値 = 0.5
