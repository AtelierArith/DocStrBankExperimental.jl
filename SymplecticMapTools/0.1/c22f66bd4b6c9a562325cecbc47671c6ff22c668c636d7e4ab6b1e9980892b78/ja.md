```
adaptive_birkhoff_extrapolation(h::Function, F::Function,
                x0::AbstractVector; rtol::Number=1e-10, Kinit = 20,
                Kmax = 100, Kstride=20, iterative::Bool=false,
                Nfactor::Integer=1, rre::Bool=true)
```

適応的に `birkhoff_extrapolation` を適用して、十分なフィルタ長 `K` を見つけます。「十分な」とは、`rtol` オプション引数によって定義されます。

引数:

  * `h`: 観測可能な関数（デフォルトの `h = (x)->x` を選択できます）
  * `F`: シンプレクティック写像
  * `x0`: 軌道の初期点
  * `rtol`: 収束のために必要な許容誤差（不正確な写像はしばしば緩い許容誤差を必要とします）
  * `Kinit`: 初期フィルタの長さ
  * `Kmax`: 許可される最大フィルタサイズ
  * `Kstride`: `birkhoff_extrapolation` の適用間で `K` が増加する量
  * `iterative`: 外挿ステップでハンケル系を解くために反復法を使用するかどうか
  * `Nfactor`: 外挿アルゴリズムがどれだけ長方形であるか。1以上でなければなりません。
  * `rre`: 最小多項式外挿の代わりに縮小ランク外挿を使用するには、true に設定します。

出力:

  * `c`: 線形モデル / フィルタ
  * `sums`: 各ウィンドウに適用された外挿値
  * `resid`: 最小二乗残差
  * `xs`: 時系列 `x[:,n] = Fⁿ(x[:,0])`
  * `hs`: 観測値 `h[:,n] = h(x[:,n])`
  * `rnorm`: resid のノルム
  * `K`: フィルタの最終次数
  * `history`: `iterative=true` の場合に返されます。最終 LSQR 反復の履歴
