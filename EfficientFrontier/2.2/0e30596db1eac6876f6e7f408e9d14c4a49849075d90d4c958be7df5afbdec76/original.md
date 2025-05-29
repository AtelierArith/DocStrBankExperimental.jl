```
    cbCL!(aCL::Vector{sCL{T}}, PS::Problem{T}; nS=Settings(PS), oneCL=true, K=PS.M+PS.J+1, kwargs...) where T
```

compute one or all (oneCL=false, K=PS.M) the Critical Line Segments by enumerating (combinations of Status). Save the CL(s) to aCL if done

See also [`SimplexCL!`](@ref), [`Problem`](@ref), [`Settings`](@ref)
