```julia
struct ALSTruncation
```

アルゴリズム構造体は、ボンドの交互最小二乗（ALS）最適化のためのものです。

## フィールド

  * `trscheme::TensorKit.TruncationScheme`
  * `maxiter::Int64`
  * `tol::Float64`
  * `check_interval::Int64`

## コンストラクタ

```
ALSTruncation(; kwargs...)
```

トランケーションアルゴリズムは、以下のキーワード引数から構築できます：

  * `trscheme::TensorKit.TruncationScheme`: ボンドによって接続されたトランケートテンソルを初期化する際のSVDトランケーションスキーム。
  * `maxiter::Int=50` : ALSイテレーションの最大数。
  * `tol::Float64=1e-15` : ALSは、2つのFETイテレーション間の忠実度の変化が`tol`より小さいときに収束します。
  * `check_interval::Int=0` : 情報を出力するためのイテレーション数を設定します。`check_interval <= 0`のときは出力が抑制されます。
