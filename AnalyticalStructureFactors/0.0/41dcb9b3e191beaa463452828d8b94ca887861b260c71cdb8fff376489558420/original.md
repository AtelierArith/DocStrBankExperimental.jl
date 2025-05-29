```
S_SALR_RPA(ϕ::T, amplitude_attr::T, inv_screening_length_attr::T, amplitude_rep::T, inv_screening_length_rep::T) where {T<:AbstractFloat}
```

Retorna una función `f(k)` que calcula el factor de estructura estático para un fluido con potencial SALR utilizando la RPA. Los parámetros del sistema y del potencial SALR se fijan.

# Arguments

  * `ϕ::T`: Fracción de volumen de las esferas.
  * `amplitude_attr::T`: Amplitud del componente atractivo de Yukawa.
  * `inv_screening_length_attr::T`: Longitud de apantallamiento inversa del componente atractivo.
  * `amplitude_rep::T`: Amplitud del componente repulsivo de Yukawa.
  * `inv_screening_length_rep::T`: Longitud de apantallamiento inversa del componente repulsivo.

# Returns

  * `Function`: Una función que toma un vector de onda `k` y retorna `S(k)`.
