`itersolve(clauses; vars::Integer=-1, verbose::Integer=0, proplimit::Integer=0, num_threads::Integer=Sys.CPU_THREADS)`

  * `vars` - 変数の数
  * `verbose` - 詳細度
  * `proplimit` - 無視される
  * `num_threads` - 使用するCPUスレッドの数

すべての解に対する反復可能なオブジェクトを返します。

```julia
julia> import CryptoMiniSat
julia> cnf = [[1, -5, 4], [-1, 5, 3, 4], [-3, -4]];
julia> collect(CryptoMiniSat.itersolve(cnf))
18-element Array{Any,1}:
 [-1, -2, -3, -4, -5]
 [-1, 2, -3, -4, -5]
 [-1, 2, 3, -4, -5]
 [1, 2, 3, -4, 5]
 [-1, -2, -3, 4, -5]
 [1, -2, 3, -4, 5]
 [-1, -2, -3, 4, 5]
 [-1, 2, -3, 4, -5]
 [1, -2, -3, 4, 5]
 [1, 2, -3, 4, 5]
 [1, 2, -3, 4, -5]
 [-1, 2, -3, 4, 5]
 [1, -2, -3, 4, -5]
 [1, -2, 3, -4, -5]
 [-1, -2, 3, -4, -5]
 [1, 2, -3, -4, 5]
 [1, -2, -3, -4, 5]
 [1, 2, 3, -4, -5]
```
