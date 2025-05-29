```
remove_all_but!(solver::GenericSolver, path::Vector{Int}, new_domain::BitVector)
```

`path`にある穴のドメインを`new_domain`に減少させます。`path`が穴を指していると仮定されており、そうでない場合は例外がスローされます。`new_domain` ⊆ `domain`であると仮定されます。例えば: [1, 0, 1, 0] ⊆ [1, 0, 1, 1]
