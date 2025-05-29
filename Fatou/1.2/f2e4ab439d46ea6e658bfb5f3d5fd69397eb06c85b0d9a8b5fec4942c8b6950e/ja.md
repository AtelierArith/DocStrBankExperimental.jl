```
newton(::Expr;                        # プライマリーマップ, (z, c) -> F
  C::Expr     = :((angle(z)/(2π))*n^p)# カラーリング, (z, n=iter., p=exp.) -> C
  ∂    = π/2, # Array{Float64,1}      # 境界, [x(a),x(b),y(a),y(b)]
  n::Integer  = 176,                  # 水平グリッドポイント
  N::Integer  = 35,                   # 最大反復回数
  ϵ::Number   = 4,                    # 流域ϵ-制限基準
  iter::Bool  = false,                # 反復モードの切り替え
  p::Number   = 0,                    # 反復カラー指数
  m::Number   = 0,                    # ニュートン重複度係数
  mandel::Bool= false,                # マンデルブロットモードの切り替え
  seed::Number= 0.0+0.0im,            # マンデルブロットシード値
  x0          = nothing,              # 軌道の開始点
  orbit::Int  = 0,                    # 軌道のコブウェブ深度
  depth::Int  = 1,                    # 関数合成の深度
  cmap::String= "",                   # imshowカラーマップ
  plane::Bool = false,                # 入力ディスクを半平面に変換
  disk::Bool  = false)                # 出力半平面をディスクに変換
```

`Fatou`におけるニュートン流域の定義

# 例

```Julia
julia> newton("z^3-1",n=800,cmap="brg")
```
