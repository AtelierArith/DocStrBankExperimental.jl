`itersolve(clauses; vars::Integer=-1, verbose::Integer=0, proplimit::Integer=0)`

  * `vars` - 変数の数
  * `verbose` - `verbose > 0` のときに、ソルバーログを `STDOUT` に印刷し、詳細が増加します。
  * `proplimit` - 実行時間を制限するのに役立ちます。伝播の数と解決時間はおおよそ線形に関連しています。0（デフォルト）の値は、無制限の伝播を許可します。

すべての解に対する反復可能なオブジェクトを返します。ユーザー定義の伝播制限が指定されている場合、イテレータはすべての実行可能な解を生成しない可能性があります。

```julia
julia> import PicoSAT
julia> cnf = Any[[1, -5, 4], [-1, 5, 3, 4], [-3, -4]];
julia> PicoSAT.itersolve(cnf)
julia> for sol in PicoSAT.itersolve(cnf)
           println(sol)
       end
[1,-2,-3,-4,5]
[1,-2,-3,4,-5]
[1,-2,-3,4,5]
[1,-2,3,-4,-5]
...
```
