```julia
randSampling(A::Matrix, B=I::Matrix; k=0::Int)
```

Generate a random sampling random Matrix `S`, E(SS')=I. ASS'B is typically used to approximate AB.

# Examples

```julia
S = randSampling(rand(2,3),rand(3,2),k=2)

3×2 Matrix{Float64}:
 0.0      0.0
 0.0      1.2439
 1.15342  0.0
```
