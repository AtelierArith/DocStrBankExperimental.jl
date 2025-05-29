```
mandelbrot(::Expr;                    # プライマリーマップ, (z, c) -> F
  Q::Expr     = :(abs2(z)),           # エスケープ基準, (z, c) -> Q
  C::Expr     = :(exp(-abs(z))*n^p),  # カラーリング, (z, n=iter., p=exp.) -> C
  ∂    = π/2, # Array{Float64,1}      # 範囲, [x(a),x(b),y(a),y(b)]
  n::Integer  = 176,                  # 水平方向のグリッドポイント
  N::Integer  = 35,                   # 最大反復回数
  ϵ::Number   = 4,                    # 流域ϵ-リミット基準
  iter::Bool  = false,                # 反復モードの切り替え
  p::Number   = 0,                    # 反復カラー指数
  m::Number   = 0,                    # ニュートンの重複度因子
  seed::Number= 0.0+0.0im,            # マンデルブロ seed 値
  x0          = nothing,              # 軌道の開始点
  orbit::Int  = 0,                    # 軌道のコブウェブの深さ
  depth::Int  = 1,                    # 関数合成の深さ
  cmap::String= "",                   # imshow カラーマップ
  plane::Bool = false,                # 入力ディスクを半平面に変換
  disk::Bool  = false)                # 出力半平面をディスクに変換
```

`Fatou` におけるマンデルブロ流域の定義

# 例

```Julia
mandelbrot(:(z^2+c),n=800,N=20,∂=[-1.91,0.51,-1.21,1.21],cmap="nipy_spectral")
```
