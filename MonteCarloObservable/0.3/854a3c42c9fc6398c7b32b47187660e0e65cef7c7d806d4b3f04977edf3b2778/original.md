```
iswithinerrorbars(A::AbstractArray{T<:Number}, B::AbstractArray{T<:Number}, Δ::AbstractArray{<:Real}[, print=false])
```

Elementwise check whether `A` and `B` are equal up to given real error matrix `Δ`. Will print `A ≈ B + K.*Δ` for `print=true`.
