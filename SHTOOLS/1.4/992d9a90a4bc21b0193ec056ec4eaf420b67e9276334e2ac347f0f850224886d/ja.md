```
PlSchmidt_d1!(p::AbstractVector{Cdouble},
               dp::AbstractVector{Cdouble}, 
               lmax::Integer,
               z::Union{AbstractFloat,Integer};
               exitstatus::Union{Nothing,Ref{<:Integer}}=nothing)
```

シュミット正規化された関連レジェンドル関数とその一次導関数をすべて計算します。

関連情報: [`PlSchmidt_d1`](@ref), [`PlSchmidt_d1`](@ref), [`PlmSchmidt_d1!`](@ref), [`PlBar_d1!`](@ref), [`PlON_d1!`](@ref), [`PLegendre_d1!`](@ref)
