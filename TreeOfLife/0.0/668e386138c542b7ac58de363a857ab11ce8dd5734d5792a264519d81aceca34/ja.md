```
cutfromroot(tree::ChronoTree, dist::Real; keep::Symbol=:both)
	:: Union{Vector{NTuple{2,Int}}, Vector{Int}}
```

ルートが誕生してから `dist` 時間単位後の時間的セクションを見つけます。引数 `keep` は、4つのオプションの中から設定できます。すなわち、`:both`（親と子を含むタプル）、`:parent`、`:child`、または `:closer` です。
