*カーネル*は、測定値を返す関数です。

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

この関数はエクスポートされていません。なぜなら「カーネル」には他にも多くの意味があるからです。例えば、https://github.com/JuliaGaussianProcesses/KernelFunctions.jl ではこの用語の別の一般的な使い方が見られます。

# 参考

  * https://en.wikipedia.org/wiki/Markov_kernel
