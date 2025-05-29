```
ConstrainedBlackBoxControlMap
```

A constrained black-box control map of the form

$$
    (x, u) ↦ h(x, u), x ∈ \mathcal{X}, u ∈ \mathcal{U}.
$$

### Fields

  * `dim`  – state dimension
  * `input_dim` – input dimension
  * `output_dim` – output dimension
  * `h` – output function
  * `X` – state constraints
  * `U` – input constraints
