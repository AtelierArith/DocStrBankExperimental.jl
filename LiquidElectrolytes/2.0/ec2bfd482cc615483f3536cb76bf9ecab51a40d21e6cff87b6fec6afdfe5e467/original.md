```
DGML_gamma!(γ, c, p, electrolyte)
```

Activity coefficients according to Dreyer, Guhlke, Müller, Landstorfer.

$$
γ_i = \exp\left(\frac{\tilde v_i p}{RT}\right) \left(\frac{\bar c}{c_0}\right)^{m_i} \frac{1}{v_0\bar c}
$$

Input:

  * c: vector of concentrations
  * p: pressure
  * electrolyte: instance of [`ElectrolyteData`](@ref)

Output: 

  * γ (mutated) activity coefficients
