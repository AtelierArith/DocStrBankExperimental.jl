```
vector_mpe_backslash(x::AbstractArray, K::Integer)
```

BirkhoffベクトルMPEをLSQRアルゴリズムを使用してシーケンス`x_n = x[:, n]`に適用します。現在、前処理は行われておらず、そのため`vector_mpe_backslash`よりも精度が低くなっています。

引数:

  * `x`: シーケンス
  * `K`: フィルタ内の未知数の数
  * `c0`: 初期推定値
  * `atol`, `btol`: 許容誤差。`IterativeSolvers.lsqr!`を参照してください。
