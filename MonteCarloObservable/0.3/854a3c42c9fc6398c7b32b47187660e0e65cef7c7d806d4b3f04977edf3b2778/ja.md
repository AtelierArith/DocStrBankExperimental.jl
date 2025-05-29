```
iswithinerrorbars(A::AbstractArray{T<:Number}, B::AbstractArray{T<:Number}, Δ::AbstractArray{<:Real}[, print=false])
```

要素ごとに `A` と `B` が与えられた実誤差行列 `Δ` まで等しいかどうかをチェックします。 `print=true` の場合は `A ≈ B + K.*Δ` を出力します。
