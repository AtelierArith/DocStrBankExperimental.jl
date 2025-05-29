```
S_Yukawa_RPA(ϕ::T, amplitude::T, inv_screening_length::T) where {T<:AbstractFloat}
```

Retorna una función `f(k)` que calcula el factor de estructura estático para un fluido con potencial de Yukawa utilizando la RPA. Los parámetros del sistema y del potencial (ϕ, amplitud, longitud de apantallamiento inversa) se fijan.

# Arguments

  * `ϕ::T`: Fracción de volumen de las esferas.
  * `amplitude::T`: Amplitud efectiva del potencial de Yukawa.
  * `inv_screening_length::T`: Longitud de apantallamiento inversa adimensional (z).

# Returns

  * `Function`: Una función que toma un vector de onda `k` y retorna `S(k)`.
