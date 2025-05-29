```
reenergise!(eco::Ecosystem, budget::Union{Float64, Unitful.Quantity{Float64}}, grid::Tuple{Int64, Int64})
```

エコシステム `eco` を、予算値 `budget` からのエネルギーで再充電し、グリッドサイズを指定する関数です。
