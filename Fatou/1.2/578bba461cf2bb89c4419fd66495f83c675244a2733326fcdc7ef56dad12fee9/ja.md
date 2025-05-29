```
juliafill(::Expr;                     # プライマリーマップ, (z, c) -> F
  Q::Expr     = :(abs2(z)),           # エスケープ基準, (z, c) -> Q
  C::Expr     = :((angle(z)/(2π))*n^p)# 色付け, (z, n=iter., p=exp.) -> C
  ∂    = π/2, # Array{Float64,1}      # 境界, [x(a),x(b),y(a),y(b)]
  n::Integer  = 176,                  # 水平方向のグリッドポイント
  N::Integer  = 35,                   # 最大反復回数
  ϵ::Number   = 4,                    # 流域 ϵ-制限基準
  iter::Bool  = false,                # 反復モードの切り替え
  p::Number   = 0,                    # 反復色指数
  x0          = nothing,              # 軌道の開始点
  orbit::Int  = 0,                    # 軌道のコブウェブの深さ
  depth::Int  = 1,                    # 関数合成の深さ
  cmap::String= "",                   # imshow カラーマップ
  plane::Bool = false,                # 入力ディスクを半平面に変換
  disk::Bool  = false)                # 出力半平面をディスクに変換
```

`Fatou` における塗りつぶされたジュリア集合を定義

# 例

```Julia
julia> juliafill("z^2-0.06+0.67im",∂=[-1.5,1.5,-1,1],N=80,n=1501,cmap="RdGy")
```
