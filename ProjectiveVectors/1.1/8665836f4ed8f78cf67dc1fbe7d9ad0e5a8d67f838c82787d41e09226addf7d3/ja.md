```
fubini_study(v::PVector{<:Number,N}, w::PVector{<:Number, N})
```

各成分 `vᵢ` と `wᵢ` の間のフビニ-スタディ距離を計算します。これは $\arccos|⟨vᵢ,wᵢ⟩|$ と定義されます。
