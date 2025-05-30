```
GridSpec(category="PeriodicDomain",path=tempname(); ID=:unknown)
```

  * ID（キーワード）またはカテゴリによって、事前定義されたグリッドのいずれかを選択します。
  * グリッドファイルにアクセスできるパス（`path`）を含む、対応する `gcmgrid` 仕様を返します。

1. `ID` による選択

  * `:LLC90`
  * `:CS32`
  * `:onedegree`
  * `:default`

例:

```
using MeshArrays
g = GridSpec(ID=:LLC90)
```

注：これらの完全にサポートされたグリッドへのパスは、`MeshArrays.jl` 内部で処理されます。

2. `category` と `path` による選択

  * `"PeriodicDomain"`
  * `"PeriodicChannel"`
  * `"CubeSphere"`
  * `"LatLonCap"`

例:

```jldoctest; output = false
using MeshArrays
g = GridSpec()
g = GridSpec("PeriodicChannel",MeshArrays.GRID_LL360)
g = GridSpec("CubeSphere",MeshArrays.GRID_CS32)
g = GridSpec("LatLonCap",MeshArrays.GRID_LLC90)
isa(g,gcmgrid)

# output

true
```
