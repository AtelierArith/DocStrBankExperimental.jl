2Dメッシュの基本構造

```
Bmesh2D(etype::Symbol,nn::Int64,ne::Int64,coord::Matrix{Float64},connect::Matrix{Int64},
        Lx::Float64, Ly::Float64, nx::Int64, ny::Int64)
```

ここで：

```
etype   = :truss2D または :solid2D
nn      = ノードの数
ne      = 要素の数
coord   = ノード座標 (x y) の nn x 2 行列
connect = 要素接続の ne x {2,4} 行列。:truss2D の場合は 2、:solid2D の場合は 4
Lx      = 水平方向 (X) の長さ (長方形の領域を使用する場合)
nx      = 水平方向の分割数 (要素)
Ly      = 垂直方向 (Y) の長さ (長方形の領域を使用する場合)
ny      = 垂直方向の分割数 (要素)
```
