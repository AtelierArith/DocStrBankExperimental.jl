```
remove_all_but!(solver::GenericSolver, path::Vector{Int}, rule_index::Int)
```

`path`にある穴を`rule_index`のルールで埋めます。`path`が穴を指していることが前提であり、そうでない場合は例外がスローされます。`rule_index`は`hole.domain`に含まれていると仮定します。

!!! warning: `hole`が現在のツリーに存在することが知られている場合、穴を直接渡すことができます。呼び出し元は、提供された`path`に実際に穴のインスタンスが存在することを確認する必要があります。
