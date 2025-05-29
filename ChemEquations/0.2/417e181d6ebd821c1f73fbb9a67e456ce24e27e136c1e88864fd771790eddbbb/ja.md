```julia
struct Compound
```

  * `tuples::Vector{Tuple{String, Int64}}`
  * `charge::Int64`

化合物の元素と電荷を構造化された方法で保存します。

!!! info
    電子は `"e"` として保存されます。

