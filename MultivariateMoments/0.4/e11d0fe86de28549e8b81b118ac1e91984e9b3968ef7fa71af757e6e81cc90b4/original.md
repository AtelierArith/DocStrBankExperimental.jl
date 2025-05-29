```
struct ImageSpaceSolver{A<:LowRankLDLTAlgorithm,S<:MacaulayNullspaceSolver}
    ldlt::A
    null::S
end
```

Computes the image space of the moment matrix using `ldlt` and then solve it with `null`.
