```
basin(::Fatou.Define, ::Integer)
```

Output the `j`-th basin of `Fatou.Define` as LaTeX. Each subsequent iteration of the Newton-Raphson method will yield a more complicated set.

# Examples

```Julia
julia> basin(newton("z^3-1"),2)
L"$\displaystyle D_2(\epsilon) = \left\{z\in\mathbb{C}:\left|\,z - \frac{\left(z - \frac{z^{3} - 1}{3 z^{2}}\right)^{3} - 1}{3 \left(z - \frac{z^{3} - 1}{3 z^{2}}\right)^{2}} - \frac{z^{3} - 1}{3 z^{2}} - r_i\,\right|<\epsilon,\,\forall r_i(\,f(r_i)=0 )\right\}$"
```
