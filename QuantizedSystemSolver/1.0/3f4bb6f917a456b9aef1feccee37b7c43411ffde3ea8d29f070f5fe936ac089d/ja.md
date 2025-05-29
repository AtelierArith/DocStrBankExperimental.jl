```
EventDependencyStruct
```

イベント依存情報を保持する構造体です。以下のフィールドがあります：

  * `id::Int:` イベントのID
  * `evCont::Vector{Int}:` HDおよびHZに使用されるインデックス追跡。イベント内でxが変更されたときにq、量子、次の再計算を更新するためにも使用されます
  * `evDisc::Vector{Int}:` HDおよびHZに使用されるインデックス追跡。
  * `evContRHS::Vector{Int}:` イベントを実行する前に他のQを更新するために使用されるインデックス追跡
