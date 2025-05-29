```
LinearTarget{D}(intercept, gradient)
```

Callable object that returns a Linear target function with `intercept` and `gradient`, and varying along direction `D`, i.e.,

```
intercept + D * gradient
```

# Example

Create a linear target function varying in `z`, equal to `0` at `z=0` and with gradient 10⁻⁶:

```julia
julia> target = LinearTarget{:z}(intercept=0, gradient=1e-6)
```
