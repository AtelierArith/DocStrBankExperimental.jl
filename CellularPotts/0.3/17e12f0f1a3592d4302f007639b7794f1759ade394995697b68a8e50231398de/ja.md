```
CellSpace(gridSize::NTuple{N, T}; periodic=true, diagonal=false)
CellSpace(gridSize::T...; periodic=true, diagonal=false) where T<:Integer
```

基礎となる空間が占めるセルを格納する具体的な型です。

`CellSpace()`は、次元のタプルを供給するか、各次元のために複数の引数を渡すことで作成できます。例えば、`CellSpace((3,3,4))`または`CellSpace(3,3,4)`のように使用します。2つのオプションのキーワード引数があります：

  * periodic `::Bool`: グリッドが周期的境界を持つかどうかを決定します
  * diagonal `::Bool`: 隣接するセルはフォン・ノイマン（デフォルト）またはムーアの近傍を持つことができます。フォン・ノイマンの近傍は**隣接する対角位置**を含みません。
