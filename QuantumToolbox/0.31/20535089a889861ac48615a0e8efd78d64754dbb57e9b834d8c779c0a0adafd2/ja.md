```
displace(N::Int, α::Number)
```

生成する [変位演算子](https://en.wikipedia.org/wiki/Displacement_operator):

$$
\hat{D}(\alpha)=\exp\left( \alpha \hat{a}^\dagger - \alpha^* \hat{a} \right),
$$

ここで、$\hat{a}$ はボソニック消滅演算子であり、$\alpha$ は光学位相空間における変位の量です。
