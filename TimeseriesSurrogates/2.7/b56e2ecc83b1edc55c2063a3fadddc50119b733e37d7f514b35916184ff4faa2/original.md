```
SNLST(n_steps, x₀, k)
```

Dynamically linear process transformed by a strongly nonlinear static transformation (SNLST)[^1].

## Equations

The system is by the following map:

$$
x(t) = k x(t-1) + a(t)
$$

with the transformation $s(t) = x(t)^3$.

# References

[^1]: Lucio et al., Phys. Rev. E *85*, 056202 (2012). [https://journals.aps.org/pre/abstract/10.1103/PhysRevE.85.056202](https://journals.aps.org/pre/abstract/10.1103/PhysRevE.85.056202)
