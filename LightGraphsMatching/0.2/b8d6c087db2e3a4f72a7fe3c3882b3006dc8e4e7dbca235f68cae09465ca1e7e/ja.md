```
struct MatchingResult{U}
    weight::U
    mate::Vector{Int}
end
```

マッチングアルゴリズムの結果を表す型です。

```
weight: マッチングの総重量

mate:    `mate[i] = j` は、頂点 `i` が頂点 `j` にマッチングされていることを示します。
         マッチングされていない頂点の場合は `mate[i] = -1` です。
```
