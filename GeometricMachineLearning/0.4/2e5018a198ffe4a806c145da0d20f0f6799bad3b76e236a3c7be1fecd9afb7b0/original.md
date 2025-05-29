```
PoissonTensor(n2)
```

Returns a (canonical) Poisson tensor of size $2n\times2n$:

$$
\mathbb{J}_{2n} = \begin{pmatrix}
\mathbb{O} & \mathbb{I}_n \\
-\mathbb{I}_n & \mathbb{O} \\
\end{pmatrix}
$$

# Arguments

It can also be called with a `backend` and a `type`:

```jldoctest
using GeometricMachineLearning

backend = CPU()
T = Float16

PoissonTensor(backend, 4, T)

# output

4×4 PoissonTensor{Float16, Matrix{Float16}}:
  0.0   0.0  1.0  0.0
  0.0   0.0  0.0  1.0
 -1.0   0.0  0.0  0.0
  0.0  -1.0  0.0  0.0
```
