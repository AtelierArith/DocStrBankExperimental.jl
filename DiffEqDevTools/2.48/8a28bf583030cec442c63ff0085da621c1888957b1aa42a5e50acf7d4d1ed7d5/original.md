`stability_region(z, tab::ODERKTableau; embedded = false)`

Calculates the stability function from the tableau at `z`. Stable if <1. If `embedded = true`, the stability function is calculated for the embedded method. Otherwise, the stability function is calculated for the main method (default).

$$
r(z) = 1 + z bᵀ(I - zA)⁻¹ e
$$

where e denotes a vector of ones.
