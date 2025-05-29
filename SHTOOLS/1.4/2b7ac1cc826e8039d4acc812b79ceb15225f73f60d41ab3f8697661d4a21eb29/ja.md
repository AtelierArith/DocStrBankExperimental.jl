```
value = MakeGridPoint(cilm::AbstractArray{Cdouble,3},
                      lmax::Integer,
                      lat::Union{AbstractFloat,Integer},
                      long::Union{AbstractFloat,Integer};
                      norm::Integer=1,
                      csphase::Integer=1,
                      dealloc::Bool=false)
value::Float64

value = MakeGridPoint(cilm::AbstractArray{Complex{Cdouble},3},
                      lmax::Integer,
                      lat::Union{AbstractFloat,Integer},
                      long::Union{AbstractFloat,Integer};
                      norm::Integer=1,
                      csphase::Integer=1,
                      dealloc::Bool=false)
value::Complex{Float64}
```

実数または複素数の球面調和関数で表現された関数を単一の点で評価します。

参照: [`SHExpandLSQ!`](@ref), [`SHExpandLSQ`](@ref), [`MakeGrid2d!`](@ref), [`MakeGrid2d`](@ref)
