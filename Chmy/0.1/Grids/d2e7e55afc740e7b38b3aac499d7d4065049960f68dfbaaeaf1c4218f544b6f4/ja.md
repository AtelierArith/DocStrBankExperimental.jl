```
UniformGrid(arch; origin, extent, dims, topology=nothing)
```

指定された原点、範囲、次元、およびトポロジーを持つ均一グリッドを構築します。

## 引数

  * `arch::Architecture`: 関連するアーキテクチャ。
  * `origin::NTuple{N,Number}`: グリッドの原点。
  * `extent::NTuple{N,Number}`: グリッドの範囲。
  * `dims::NTuple{N,Integer}`: グリッドの次元。
  * `topology=nothing`: グリッドのトポロジー。提供されない場合、デフォルトの `Bounded` トポロジーが使用されます。
