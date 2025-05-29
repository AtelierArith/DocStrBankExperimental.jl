```
(dmatrixf2c, IX) = fine2coarse!(GP::GraphPart;
dmatrix::Array{Float64,3} = zeros(0, 0, 0),
coefp::Bool = false, indp::Bool = false)
```

グラフパートオブジェクトにファインからコースへの情報（rs2f2c、tagf2c、およびcompinfof2c）を埋め込みます。また、展開係数の行列を再配置します。

### 入力引数

  * `GP::GraphPart`: ファインからコースへの情報（rsf2c、tagf2c、compinfof2c）がない入力GraphPartオブジェクト。この関数の後、rsf2c、tagf2c、compinfof2cが埋められます。rs、tag、compinfoはそのままです。
  * `dmatrix::Array{Float64,3}`: コースからファインへの配置の展開係数の行列（デフォルト：ヌル行列）
  * `coefp::Bool`: 再配置されたf2c係数を返すフラグ（デフォルト：false）
  * `indp::Bool`: 再順序付けインデックスを返すフラグ（デフォルト：false）

### 出力引数

  * `dmatrixf2c::Array{Float64,3}`: ファインからコースへの配置の展開係数の行列（要求された場合）
  * `IX::Vector{Unsigned}`: すべてのレベルの再順序付けインデックス
