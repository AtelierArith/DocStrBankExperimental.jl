```
suchthat(;left::AbstractString = nothing, right::AbstractString = nothing, rightlen::Int = nothing, right_is_suffix_of::AbstractString = nothing)::Array
```

引数として与えられた生成物が、名前付き引数で与えられたすべての述語を満たす場合に `true` を返す（`true` または `false` を返す一引数関数である）述語。
