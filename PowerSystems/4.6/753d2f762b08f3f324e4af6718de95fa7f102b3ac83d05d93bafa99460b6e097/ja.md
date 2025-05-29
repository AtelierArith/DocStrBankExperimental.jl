```
mutable struct Arc <: Topology
    from::Bus
    to::Bus
    internal::InfrastructureSystemsInternal
end
```

2つのバスを接続するトポロジカルな有向エッジです。

アークは、ラインやトランスフォーマーを定義する際に `from` と `to` バスを定義するために使用されます。

# 引数

  * `from::Bus`: 初期バス
  * `to::Bus`: 終端バス
  * `internal::InfrastructureSystemsInternal`: (**変更しないでください。**) PowerSystems.jl 内部参照
