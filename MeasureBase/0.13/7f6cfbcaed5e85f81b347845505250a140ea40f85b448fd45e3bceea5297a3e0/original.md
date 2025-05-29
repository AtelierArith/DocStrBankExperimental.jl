A *kernel* is a function that returns a measure.

```
k1 = kernel() do x
    Normal(x, x^2)
end

k2 = kernel(Normal) do x
    (μ = x, σ = x^2)
end

k3 = kernel(Normal; μ = identity, σ = abs2)

k4 = kernel(Normal; μ = first, σ = last) do x
    (x, x^2)
end

x = randn(); k1(x) == k2(x) == k3(x) == k4(x)
```

This function is not exported, because "kernel" can have so many other meanings. See for example https://github.com/JuliaGaussianProcesses/KernelFunctions.jl for another common use of this term.

# Reference

  * https://en.wikipedia.org/wiki/Markov_kernel
