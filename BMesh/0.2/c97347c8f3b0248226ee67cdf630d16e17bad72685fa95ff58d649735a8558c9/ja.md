2D背景メッシュを生成する :truss2D 要素のための

```
Bmesh_truss_2D(Lx::Float64, nx::Int64, Ly::Float64, ny::Int64)
```

ここで

```
Lx  = X方向の長さ（横方向）
nx  = X方向の分割数（要素数）
Ly  = Y方向の長さ（縦方向）
ny  = Y方向の分割数（要素数）
```

は次のように返します

```
Bmesh2D(:truss2D,nn,ne,coord,connect,Lx,Ly, nx,ny)
```

ここで

```
nn      = ノードの数 
ne      = 要素の数
coord   = ノード座標 (x y) の nn x 2 行列 
connect = 接続性の ne x 2 行列
```

ノードは左下 (0,0) から右下 (0,Lx) まで、行ごとに作成されます。 水平要素が最初に生成され、その後に垂直要素、対角線 /、そして他の対角線が生成されます。
