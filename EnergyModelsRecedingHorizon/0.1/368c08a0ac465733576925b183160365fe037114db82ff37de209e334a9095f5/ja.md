```
get_future_value(𝒳ᵛᵉᶜ::Vector{Vector})
get_future_value(case::Case)
get_future_value(𝒰::UpdateCase)
```

ケース `case` の FutureValue のベクトルまたは要素ベクトル `𝒳ᵛᵉᶜ` のベクトルを返します。

入力が [`UpdateCase`](@ref) の場合、UpdateCase `𝒰` の個々の [`FutureValueSub`](@ref) タイプの **新しい** `FutureValues` を返します。
