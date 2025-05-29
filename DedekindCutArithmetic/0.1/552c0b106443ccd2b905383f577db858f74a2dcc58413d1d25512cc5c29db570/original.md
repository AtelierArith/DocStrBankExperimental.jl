Macro to construct a [`DedekindCut`](@ref).

A cut is defined using the following syntax

```julia
@cut x ∈ [a, b], low, high
```

This defines a real number $x$ in the interval $[a, b]$ which is approximated by the inequality $φ(x)$ from below and $ψ(x)$ from above.

$φ$ and $ψ$ can be any julia expression, also referring to variables in the scope where the macro is called.

Similarly, $a$ and $b$ can also be julia expressions, but they cannot depend on $x$.
