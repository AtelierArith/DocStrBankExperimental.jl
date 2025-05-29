```
WolfePowellBinaryLinesearch <: Linesearch
```

A [`Linesearch`](@ref) method that determines a step size `t` fulfilling the Wolfe conditions

based on a binary chop. Let $η$ be a search direction and $c1,c_2>0$ be two constants. Then with

$$
A(t) = f(x_+) ≤ c1 t ⟨\operatorname{grad}f(x), η⟩_{x}
\quad\text{and}\quad
W(t) = ⟨\operatorname{grad}f(x_+), \text{V}_{x_+\gets x}η⟩_{x_+} ≥ c_2 ⟨η, \operatorname{grad}f(x)⟩_x,
$$

where $x_+ = \operatorname{retr}_x(tη)$ is the current trial point, and $\text{V}$ is a vector transport. Then the following Algorithm is performed similar to Algorithm 7 from [Huang:2014](@cite)

1. set $α=0$, $β=∞$ and $t=1$.
2. While either $A(t)$ does not hold or $W(t)$ does not hold do steps 3-5.
3. If $A(t)$ fails, set $β=t$.
4. If $A(t)$ holds but $W(t)$ fails, set $α=t$.
5. If $β<∞$ set $t=\frac{α+β}{2}$, otherwise set $t=2α$.

# Constructors

There exist two constructors, where, when provided the manifold `M` as a first (optional) parameter, its default retraction and vector transport are the default. In this case the retraction and the vector transport are also keyword arguments for ease of use. The other constructor is kept for backward compatibility.

```
WolfePowellLinesearch(
    M=DefaultManifold(),
    c1::Float64=10^(-4),
    c2::Float64=0.999;
    retraction_method = default_retraction_method(M),
    vector_transport_method = default_vector_transport(M),
    linesearch_stopsize = 0.0
)
```
