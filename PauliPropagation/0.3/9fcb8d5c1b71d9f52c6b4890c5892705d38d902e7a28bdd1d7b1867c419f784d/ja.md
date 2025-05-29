```
ispauli(pauli1::Union{Symbol, PauliType}, pauli2::Union{Symbol, PauliType})

ispauli(pauli1::Union{Vector{Symbol}, PauliStringType}, pauli2::Union{Vector{Symbol}, PauliStringType})
```

2つのパウリが等しいかどうかを確認します。一方はシンボルとして与えられ、もう一方は整数として与えられます。
