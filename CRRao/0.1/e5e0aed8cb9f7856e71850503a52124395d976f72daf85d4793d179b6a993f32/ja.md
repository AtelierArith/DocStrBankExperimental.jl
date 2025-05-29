```julia
Probit <: CRRaoLink
```

プロビットリンク関数を表す型であり、次の式によって定義されます

$$
z\mapsto \mathbb{P}[Z\le z]
$$

ここで、$Z\sim \text{Normal}(0, 1)$です。
