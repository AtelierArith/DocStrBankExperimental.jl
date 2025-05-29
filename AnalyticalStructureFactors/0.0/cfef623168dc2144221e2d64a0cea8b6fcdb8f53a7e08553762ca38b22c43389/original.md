```
S_Yukawa_RPA(ϕ::T, amplitude::T, inv_screening_length::T, k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

Calcula el factor de estructura S(k) para un vector de valores de k.

# Arguments

  * `ϕ::T`: Fracción de volumen.
  * `amplitude::T`: Amplitud del potencial de Yukawa.
  * `inv_screening_length::T`: Longitud de apantallamiento inversa.
  * `k_values::AbstractVector{T}`: Un vector de valores de k adimensionales.

# Returns

  * `Vector{T}`: Un vector de valores de S(k) correspondientes a cada k en `k_values`.
