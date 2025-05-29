```
ObjType{name}
```

Polymer.jlで定義されたオブジェクトの型を表す型です。

`ObjType`オブジェクトは、[`make`](@ref)の最初の引数に渡すことができ、`name`で指定されたオブジェクトを作成するためにこのメソッドの正しいバージョンにディスパッチします：

  * :System: PolymerSystem
  * :Component: Component
  * :χN_map: Dict{Set{Symbol},AbstractFloat}
  * :Specie: AbstractSpecie (KuhnSegment) および SmallMolecule
  * :SMOL: SmallMolecule
  * :BCP: BlockCopolymer
  * :Block: PolymerBlock
  * :BlockEnd: BlockEnd (FreeEnd および BranchPoint)
