```
get_future_value(𝒳ᵛᵉᶜ::Vector{Vector})
get_future_value(case::Case)
get_future_value(𝒰::UpdateCase)
```

Returns the vector of FutureValue of the Case `case` or the vector of elements vectors `𝒳ᵛᵉᶜ`.

If the input is an [`UpdateCase`](@ref), it returns the **new** `FutureValues`s of the individual [`FutureValueSub`](@ref) types of UpdateCase `𝒰`.
