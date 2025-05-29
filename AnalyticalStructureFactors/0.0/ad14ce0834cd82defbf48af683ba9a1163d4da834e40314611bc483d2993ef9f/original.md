```
S_SW_RPA(ϕ::T, temperature::T, lambda_range::T, k::T) where {T<:AbstractFloat}
```

Calcula el factor de estructura estático para un fluido de pozo cuadrado utilizando la Random Phase Approximation (RPA). El sistema de referencia es de esferas duras con corrección de Verlet-Weiss.

La fórmula general de RPA es: S(k) = 1 / ( 1/S₀(k) - ρ * β * u*pert*tilde(k) ) donde S₀(k) es el factor de estructura del sistema de referencia, ρ es la densidad numérica, y u*pert*tilde(k) es la transformada de Fourier de la parte perturbativa del potencial.

# Arguments

  * `ϕ::T`: Fracción de volumen de las esferas.
  * `temperature::T`: Temperatura adimensional (ej. k*B * T*abs / ε).
  * `lambda_range::T`: Rango del pozo cuadrado (λ en unidades de σ).
  * `k::T`: Vector de onda adimensional (k = qσ).

# Returns

  * `T`: Valor del factor de estructura S(k).
