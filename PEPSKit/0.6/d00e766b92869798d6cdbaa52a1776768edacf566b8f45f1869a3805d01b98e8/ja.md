```julia
struct FullEnvTruncation
```

完全環境切断（FET）のアルゴリズム構造体。

## フィールド

  * `trscheme::TensorKit.TruncationScheme`
  * `maxiter::Int64`
  * `tol::Float64`
  * `trunc_init::Bool`
  * `check_interval::Int64`

## コンストラクタ

```
FullEnvTruncation(; kwargs...)
```

切断アルゴリズムは、以下のキーワード引数から構築できます：

  * `trscheme::TensorKit.TruncationScheme` : 新しいボンド行列を最適化する際のSVD切断スキーム。
  * `maxiter::Int=50` : FETの最大反復回数。
  * `tol::Float64=1e-15` : FETは、2つのFET反復間の忠実度の変化が`tol`より小さいときに収束します。
  * `trunc_init::Bool=true` : 新しいボンド行列の初期化が古いボンド行列の切断SVDから得られるかどうかを制御します。
  * `check_interval::Int=0` : 情報を印刷するための反復回数を設定します。`check_interval <= 0`のとき、出力は抑制されます。

## 参考文献

  * [Glen Evenbly, Phys. Rev. B 98, 085155 (2018)](@cite evenbly_gauge_2018).
