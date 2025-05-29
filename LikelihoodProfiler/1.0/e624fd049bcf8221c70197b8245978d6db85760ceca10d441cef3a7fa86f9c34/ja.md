```
CICOProfiler
```

制約最適化（CICO）法による信頼区間を、しきい値との尤度関数の交点を見つけるために使用します。詳細については[CICOBase docs](https://github.com/insysbio/CICOBase.jl)を参照してください。`using CICOBase`が必要です。

### フィールド

  * `optimizer::Symbol`: 最適化プロセスに使用される最適化手法。デフォルトはNLoptの`:LN_NELDERMEAD`です。
  * `scan_tol::Float64`: エンドポイントスキャンの許容誤差。デフォルトは`1e-3`です。

### 例

```julia
profiler = CICOProfiler(optimizer = :LN_NELDERMEAD, scan_tol = 1e-3)
```
