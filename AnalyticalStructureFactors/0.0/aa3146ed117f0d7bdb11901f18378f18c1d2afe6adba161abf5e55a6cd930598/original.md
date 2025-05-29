```
S_Yukawa_RPA(ϕ::T, amplitude::T, inv_screening_length::T, k::T) where {T<:AbstractFloat}
```

Calcula el factor de estructura estático para un fluido con potencial de Yukawa utilizando la Random Phase Approximation (RPA). El sistema de referencia es de esferas duras con corrección de Verlet-Weiss.

La fórmula general de RPA es: S(k) = 1 / ( 1/S₀(k) - ρ*factor * β * u*pert*tilde(k) ) donde S₀(k) es el factor de estructura del sistema de referencia, ρ*factor es un factor relacionado con la densidad (usualmente 6ϕ/π para σ=1), y u*pert*tilde(k) es la transformada de Fourier de la parte perturbativa del potencial.

# Arguments

  * `ϕ::T`: Fracción de volumen de las esferas.
  * `amplitude::T`: Amplitud efectiva del potencial de Yukawa (a menudo incluye β, ej., βε).
  * `inv_screening_length::T`: Longitud de apantallamiento inversa adimensional (z).
  * `k::T`: Vector de onda adimensional (k = qσ).

# Returns

  * `T`: Valor del factor de estructura S(k).
