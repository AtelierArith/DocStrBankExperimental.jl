Parameters for computing saturation vapour pressure of water using the Tetens' equation,

```
eᵢ(T) = e₀ * exp(Cᵢ * (T - T₀) / (T + Tᵢ)),
```

where T is in Kelvin and i = 1, 2 for saturation above and below freezing, respectively. From Tetens (1930), and Murray (1967) for below freezing.

  * `e₀::AbstractFloat`: Saturation water vapour pressure at 0°C [Pa]
  * `T₀::AbstractFloat`: 0°C in Kelvin
  * `T₁::AbstractFloat`: Tetens denominator (water) [˚C]
  * `T₂::AbstractFloat`: Tetens denominator following Murray (1967, below freezing) [˚C]
  * `C₁::AbstractFloat`: Tetens numerator scaling [1], above freezing
  * `C₂::AbstractFloat`: Tetens numerator scaling [1], below freezing
