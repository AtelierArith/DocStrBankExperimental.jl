```
indicator(y, b; indregion=:above, ineq=:nonstrict)
```

Indicator variable of default form $\mathbf{1}\{y ≥ b\}$. The inequality can be made  strict and the direction of inequality can be reversed.

# Arguments

  * `ineq=:nonstrict` (default):  calculates $\mathbf{1}\{y ≥ b\}$ or

$\mathbf{1}\{y ≤ b\}$.

  * `ineq=:strict`: calculates $\mathbf{1}\{y > b\}$ or $\mathbf{1}\{y < b\}$.
  * `indregion=:above` (default): calculates $\mathbf{1}\{y ≥ b\}$ or

$\mathbf{1}\{y > b\}$.

  * `indregion=:below`: calculates $\mathbf{1}\{y ≤ b\}$ or $\mathbf{1}\{y < b\}$.
