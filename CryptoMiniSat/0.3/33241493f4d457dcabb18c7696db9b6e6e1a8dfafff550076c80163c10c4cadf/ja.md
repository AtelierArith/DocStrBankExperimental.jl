`solve(clauses; vars::Integer=-1, verbose::Integer=0, proplimit::Integer=0, num_threads::Int = Sys.CPU_THREADS)`

  * `vars` - 変数の数（指定されていない場合は推測されます）
  * `verbose` - 詳細度
  * `proplimit` - 無視されます
  * `num_threads` - 使用するCPUスレッドの数

問題が充足可能であれば解を返します。充足可能な解は符号付き整数のベクトルとして表されます。問題が充足不可能な場合、メソッドは `:unsatisfiable` シンボルを返します。

```julia
julia> import CryptoMiniSat
julia> cnf = [[1, -5, 4], [-1, 5, 3, 4], [-3, -4]];
julia> CryptoMiniSat.solve(cnf)
5-element Array{Int64,1}:
 -1
 -2
 -3
 -4
 -5
```
