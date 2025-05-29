```
S_SALR_RPA(ϕ::T, amplitude_attr::T, inv_screening_length_attr::T, amplitude_rep::T, inv_screening_length_rep::T, k::T) where {T<:AbstractFloat}
```

Calcula el factor de estructura estático para un fluido con potencial SALR utilizando la Random Phase Approximation (RPA). El sistema de referencia es de esferas duras con corrección de Verlet-Weiss. El potencial SALR se modela como la diferencia de dos potenciales de Yukawa: u*SALR(r) = u*Yukawa*attr(r) - u*Yukawa_rep(r).

# Arguments

  * `ϕ::T`: Fracción de volumen de las esferas.
  * `amplitude_attr::T`: Amplitud efectiva del componente atractivo de Yukawa (K_A).
  * `inv_screening_length_attr::T`: Longitud de apantallamiento inversa del componente atractivo (z_A).
  * `amplitude_rep::T`: Amplitud efectiva del componente repulsivo de Yukawa (K_R).
  * `inv_screening_length_rep::T`: Longitud de apantallamiento inversa del componente repulsivo (z_R).
  * `k::T`: Vector de onda adimensional (k = qσ).

# Returns

  * `T`: Valor del factor de estructura S(k).
