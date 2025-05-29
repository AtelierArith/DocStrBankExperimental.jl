```
mutable struct UniformIterator
```

均一木のすべての候補プログラムを列挙する内部イテレータ。

  * `solver`: 均一ソルバー。
  * `outeriter`: 均一木を生成する責任を持つ外部イテレータ。このフィールドは[`derivation_heuristic`](@ref)に基づいてディスパッチするために使用されます。
  * `unvisited_branches`: ルートから現在の探索ノードまでの各探索ノードに対して、訪問されていないブランチのリスト。
  * `nsolutions`: これまでに見つかった解の数。
