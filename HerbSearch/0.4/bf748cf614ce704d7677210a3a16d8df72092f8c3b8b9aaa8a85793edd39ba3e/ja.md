```
mutable struct TopDownIterator <: ProgramIterator
```

与えられた深さとサイズに関して、文法に従って[`Symbol`](@ref) `sym`から始まる文脈自由文法を列挙します。探索は、導出のための与えられた優先度関数と、発見されたノードのための展開関数を使用して行われます。具体的なイテレータは、以下のメソッドをオーバーロードすることができます：

  * priority_function
  * derivation_heuristic
  * hole_heuristic
