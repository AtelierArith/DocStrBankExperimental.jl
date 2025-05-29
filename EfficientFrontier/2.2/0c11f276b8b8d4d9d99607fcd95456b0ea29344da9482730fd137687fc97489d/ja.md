```
    computeCL!(aCL::Vector{sCL{T}}, S::Vector{Status}, PS::Problem{T}, nS::Settings{T}) where T
```

S::Vector{Status}のためにクリティカルラインセグメントを計算し、aCL[end]に保存します。戻り値: 完了した場合はtrue。
