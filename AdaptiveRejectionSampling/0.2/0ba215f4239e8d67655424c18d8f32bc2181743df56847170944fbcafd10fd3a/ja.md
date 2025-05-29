```
Envelop(lines::Vector{Line}, support::Tuple{Float64, Float64})
```

k セグメントで定義された区分線形関数で、線 `L_1, ..., L_k` とカットポイント `c_1, ..., c_k+1` を持ち、`c1 = support[1]` および `c2 = support[2]` です。線 L*k は区間 [c*k, c*k+1] でアクティブであり、[exp_integral](@exp_integral) に基づいて重み w*k が割り当てられます。c*1 から c*k+1 までの重み付き積分は 1 であるため、エンベロープは密度として解釈されます。
