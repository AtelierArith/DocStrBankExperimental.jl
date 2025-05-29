```
powder_average(f, cryst, radii, n; seed=0)
```

Calculate a powder-average over structure factor intensities. The `radii`, with units of inverse length, define spherical shells in reciprocal space. The [Fibonacci lattice](https://arxiv.org/abs/1607.04590) yields `n` points on the sphere, with quasi-uniformity. Sample points on different shells are decorrelated through random rotations. A consistent random number `seed` will yield reproducible results. The function `f` should accept a list of q-points and call [`intensities`](@ref) or [`intensities_static`](@ref).

# Example

```julia
radii = range(0.0, 3.0, 200)
res = powder_average(cryst, radii, 500) do qs
    intensities(swt, qs; energies, kernel)
end
plot_intensities(res)
```
