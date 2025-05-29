```
cutfromtips(tree::ChronoTree, dist::Real; 
	keep::Symbol=:both, average=minimum, reltol=1e-6) 
	:: Union{Vector{NTuple{2,Int}}, Vector{Int}}
```

根が生まれる前の `dist` 時間単位の時間的セクションを見つけます。引数 `keep` は、`:both`（親と子を含むタプル）、`:parent`、`:child`、または `:closer` の4つのオプションの中から設定できます。
