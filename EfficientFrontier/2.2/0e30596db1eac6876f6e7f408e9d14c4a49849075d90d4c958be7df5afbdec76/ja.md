```
    cbCL!(aCL::Vector{sCL{T}}, PS::Problem{T}; nS=Settings(PS), oneCL=true, K=PS.M+PS.J+1, kwargs...) where T
```

1つまたはすべての（oneCL=false, K=PS.M）クリティカルラインセグメントをステータスの組み合わせを列挙することで計算します。完了した場合、CL(s)をaCLに保存します。

[`SimplexCL!`](@ref)、[`Problem`](@ref)、[`Settings`](@ref)も参照してください。
