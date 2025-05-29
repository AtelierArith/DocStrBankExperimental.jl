```
displace(N::Int, α::Number)
```

Generate a [displacement operator](https://en.wikipedia.org/wiki/Displacement_operator):

$$
\hat{D}(\alpha)=\exp\left( \alpha \hat{a}^\dagger - \alpha^* \hat{a} \right),
$$

where $\hat{a}$ is the bosonic annihilation operator, and $\alpha$ is the amount of displacement in optical phase space.
