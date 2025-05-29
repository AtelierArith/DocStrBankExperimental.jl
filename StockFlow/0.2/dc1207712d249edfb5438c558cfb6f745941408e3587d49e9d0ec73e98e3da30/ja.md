与えられたエッジのリストがウォークである場合、すなわち各エッジのターゲットが次のエッジのソースである場合にtrueを返します。エッジの空リストはウォークと見なされます。

注意、負のエッジは正のエッジの後に来ます：

```julia-repl
julia> using StockFlow; using StockFlow.Syntax;
julia> cl = (@cl A => +B, B => -C, C => +D, D => -E);
julia> is_walk(cl, [1,3,2,4])
true
```
