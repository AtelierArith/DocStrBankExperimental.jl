```
lanczos(X,Y,n; <キーワード引数>)
```

構造を利用したランツォスに基づくSVD - nモードの行列化 (X ∗ Y)ₙ の左特異ベクトルと特異値を計算します。行列 (X ∗ Y)ₙ(X ∗ Y)ₙᵀ で動作します。

## 引数:

  * `reqrank::Integer`: 要求されるランク。オプション。
  * `variant` ∈ {'A','B'} 乗算のバリアント (X ∗ Y)ₙ(X ∗ Y)ₙᵀ。デフォルト: 'B'。
  * `tol::Number/Vector`: 許容誤差。デフォルト: 1e-8。
  * `maxit`: 最大反復回数。デフォルト: 1000。
  * `p::Integer`: オーバーサンプリングパラメータ。デフォルト p=10。
