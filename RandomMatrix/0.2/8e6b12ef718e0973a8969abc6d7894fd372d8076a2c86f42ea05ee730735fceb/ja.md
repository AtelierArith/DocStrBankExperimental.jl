```julia
randSampling(A::Matrix, B=I::Matrix; k=0::Int)
```

ランダムサンプリング行列 `S` を生成します。E(SS')=I。ASS'Bは通常、ABを近似するために使用されます。

# 例

```julia
S = randSampling(rand(2,3),rand(3,2),k=2)

3×2 Matrix{Float64}:
 0.0      0.0
 0.0      1.2439
 1.15342  0.0
```
