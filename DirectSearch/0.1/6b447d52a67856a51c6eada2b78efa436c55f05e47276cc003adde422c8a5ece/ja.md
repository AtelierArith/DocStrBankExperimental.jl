```
SetInitialPoint(p::DSProblem{T}, x::Vector{T}) where T
```

初期の候補点を `x` に設定します。これは正しい次元でなければなりません。極端なバリア制約を使用している場合は、これらの制約も満たす必要があります。
