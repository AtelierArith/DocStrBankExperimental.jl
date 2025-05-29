```
shift(bf::FloatingGTBasisFuncs{T, D, 𝑙, GN, PT, 1}, 
      dl::Union{Vector{Int}, NTuple{D, Int}, LTuple{D}}, op::Function=+) where 
     {T, D, 𝑙, GN, PT} -> 
BasisFunc{T, D, <:Any, GN, PT}
```

入力された `FloatingGTBasisFuncs` の角運動量（直交座標表現）を、各成分の変化を指定する `dl` に基づいてシフトします（デフォルトの二項演算子 `op` は `+` です）。
