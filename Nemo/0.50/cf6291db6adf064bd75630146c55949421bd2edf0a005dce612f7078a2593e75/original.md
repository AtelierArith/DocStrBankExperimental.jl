```
cyclotomic_real_subfield(n::Int, s::VarName = "(z_$n + 1/z_$n)", t = "\$"; cached = true)
```

Return a tuple $R, x$ consisting of the parent object $R$ and generator $x$ of the totally real subfield of the $n$-th cyclotomic field, $\mathbb{Q}(\zeta_n)$. The supplied string `s` specifies how the generator of the number field should be printed. If provided, the string `t` specifies how the generator of the polynomial ring from which the number field is constructed, should be printed. If it is not supplied, a default dollar sign will be used to represent the variable.
