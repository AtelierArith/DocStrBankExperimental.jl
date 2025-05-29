```
WCADivision{P<:Potential, T, UC}
```

fields

  * `potential::Potential`
  * `cutoff` : ($r_{c}$)
  * `U_c` : $U(r=r_c)$

Splits the `potential` at the cutoff point using the WCA splitting rule. This means 

$$
u(r) = u_{SR}(r) + U_{LR}(r),
$$

where $U_{LR}(r) = u(r)$ for $r > r_{c}$, and $U(r_{c})$        for $r < r_{c}$, and   $USR(r) = 0$    for $r > r_{c}$, and $U(r) - U(r_{c})$ for $r < r_{c}$.
