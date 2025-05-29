エッジのインデックスによるCausalLoopPMのソース頂点インデックスを返します。負のエッジは正のエッジの後に来ます。

`julia-repl julia> using StockFlow; StockFlow.Syntax; julia> cl = (@cl A => +B, B => -C, C => +D); julia> sedge(cl, 3) 2`` ノードはA、B、Cの順に並んでいます。エッジはA => +B、C => +D、B => -Cの順に並んでいます。したがって、3番目のエッジのソースインデックスはBであり、インデックスは2です。
