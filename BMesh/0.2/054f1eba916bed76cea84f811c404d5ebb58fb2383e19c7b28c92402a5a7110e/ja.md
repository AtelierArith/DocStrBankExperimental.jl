3Dメッシュの基本構造

```
Bmesh3D(etype::Symbol,nn::Int64,ne::Int64,coord::Matrix{Float64},connect::Matrix{Int64},
        Lx::Float64, Ly::Float64, Lz::Float64,nx::Int64, ny::Int64, nz::Int64)
```

ここで：

```
etype   = :truss2D または :solid2D
nn      = ノードの数
ne      = 要素の数
coord   = nn x 3 行列でノード座標 (x y z)
connect = ne x {2,8} 行列で要素の接続性。:truss3D の場合は 2、:solid3D の場合は 8
Lx      = 水平方向 (X) の長さ (立方体ドメインを使用する場合)
nx      = 水平方向 X 方向の分割数 (要素)
Ly      = 水平方向 (Y) の長さ (立方体ドメインを使用する場合)
ny      = 水平方向 Y 方向の分割数 (要素)
Lz      = 垂直方向 (Z) の長さ (立方体ドメインを使用する場合)
nz      = 垂直方向の分割数 (要素)
```
