`solve(clauses; vars::Integer=-1, verbose::Integer=0, proplimit::Integer=0)`

  * `vars` - 変数の数
  * `verbose` - `verbose > 0` のときに `STDOUT` にソルバーログを印刷し、詳細が増加します。
  * `proplimit` - 実行時間を制限するのに役立ちます。伝播の数と解決時間はおおよそ線形に関連しています。値が 0 (デフォルト) の場合、伝播の数に制限はありません。

問題が充足可能であれば解を返します。充足可能な解は符号付き整数のベクトルとして表されます。問題が充足不可能な場合、メソッドは `:unsatisfiable` シンボルを返します。定義された伝播制限内で解を見つけられない場合、`:unknown` シンボルが返されます。

```julia
julia> import PicoSAT
julia> cnf = Any[[1, -5, 4], [-1, 5, 3, 4], [-3, -4]];
julia> PicoSAT.solve(cnf)
5-element Array{Int64,1}:
   1
  -2
  -3
  -4
   5
```
