```
mutable struct MISProblem{INT <: Integer} <: AbstractProblem
```

最大独立集合（MIS）問題を表します。

# フィールド

  * `g::SimpleGraph`: MIS問題に関連付けられたグラフ。

# メソッド

  * `copy(p::MISProblem)`: 指定された `MISProblem` のコピーを作成します。
  * `Base.show(io::IO, p::MISProblem)`: `MISProblem` の頂点数を表示します。
