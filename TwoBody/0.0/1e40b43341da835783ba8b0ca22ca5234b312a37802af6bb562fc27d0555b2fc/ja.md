`Hamiltonian(operator1, operator2, ...)`

$$
\hat{H} = \sum_i \hat{o}_i
$$

ハミルトニアンは各ソルバーの入力です。これは原子単位系における水素原子の非相対論的ハミルトニアンの例です：

$$
\hat{H} = 
- \frac{1}{2} \nabla^2
- \frac{1}{r}
$$

```@example
H = Hamiltonian(
  NonRelativisticKinetic(ℏ =1 , m = 1),
  CoulombPotential(coefficient = -1),
)
```
