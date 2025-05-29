```
GridSpec(category="PeriodicDomain",path=tempname(); np=nothing, ID=:unknown)
```

  * ID（キーワード）またはカテゴリのいずれかで、事前定義されたグリッドの1つを選択します。
  * グリッドファイルにアクセスできるパス（`path`）を含む、対応する `gcmgrid` 仕様を返します。

1. `ID` による選択

  * `:LLC90`
  * `:CS32`
  * `:LLC270`
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

3. `np` 引数を使った `category` と `path` による選択

  * `np` は、`LatLonCap` および `CubeSphere` タイルの x または y のグリッドポイントの数です。

`np` は `LatLonCap` に対しては 90、`CubeSphere` に対しては 32 にデフォルト設定されており、カテゴリ引数を使って LLC270 グリッドにアクセスするには含める必要があります。

例:

```jldoctest; output = false
using MeshArrays
g = GridSpec("LatLonCap",MeshArrays.GRID_LLC90,np=90)
g = GridSpec("LatLonCap",MeshArrays.GRID_LLC270,np=270)
g = GridSpec("CubeSphere",MeshArrays.GRID_CS32,np=32)
isa(g,gcmgrid)

# output

true
```
