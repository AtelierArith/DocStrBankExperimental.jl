```
confint(r::AbstractDIDResult; level::Real=0.95)
```

各係数推定値の信頼区間を返します。返されるオブジェクトは `Tuple{Vector{Float64}, Vector{Float64}}` 型で、最初のベクターはすべての区間の下限を収集し、2番目のベクターは上限を収集します。
