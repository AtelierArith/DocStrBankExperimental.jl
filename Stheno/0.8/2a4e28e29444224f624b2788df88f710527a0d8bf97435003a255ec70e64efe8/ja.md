```
@gppp(model_expression)
```

コードスニペットから `GaussianProcessProbabilisticProgramme` (`GPPP`) を構築します。

```jldoctest
f = @gppp let
    f1 = GP(SEKernel())
    f2 = GP(Matern52Kernel())
    f3 = f1 + f2
end

x_local = randn(5)

x = BlockData(GPPPInput(:f1, x_local), GPPPInput(:f2, x_local), GPPPInput(:f3, x_local))

y = rand(f(x, 1e-12))

f1, f2, f3 = split(x, y)

isapprox(f1 + f2, f3; rtol=1e-4)

# output

true
```
