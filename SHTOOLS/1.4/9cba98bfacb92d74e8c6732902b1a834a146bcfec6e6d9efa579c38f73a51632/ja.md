```
cilm, lmax = SHExpandDH(griddh::AbstractArray{Cdouble,2},
                        n::Integer;
                        norm::Integer=1,
                        sampling::Integer=1,
                        csphase::Integer=1,
                        lmax_calc::Union{Nothing,Integer}=nothing,
                        exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::Array{Cdouble,3}
lmax:Int

cilm, lmax = SHExpandDH(griddh::AbstractArray{Complex{Cdouble},2},
                        n::Integer;
                        norm::Integer=1,
                        sampling::Integer=1,
                        csphase::Integer=1,
                        lmax_calc::Union{Nothing,Integer}=nothing,
                        exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
cilm::Array{Complex{Cdouble},3}
lmax:Int

DriscollとHealy（1994）のサンプリング定理を使用して、等間隔または等間隔の実数または複素数マップを実数または複素数の球面調和関数に展開します。

参照：[`SHExpandDH!`](@ref), [`MakeGridDH`](@ref), [`MakeGradientDH`](@ref)
```
