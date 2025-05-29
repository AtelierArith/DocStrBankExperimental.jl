```
onehotbatch(target)
```

Performs a one-hot-batch encoding of a vector of integers: $input\in\{0,1,\ldots,9\}^\ell$. 

The output is a tensor of shape $10\times1\times\ell$.

If the input is $0$, this function produces:

$$
0 \mapsto \begin{bmatrix} 1 & 0 & \ldots & 0 \end{bmatrix}^T.
$$

In more abstract terms: $i \mapsto e_i$.

# Examples

```jldoctest
using GeometricMachineLearning: onehotbatch

target = [0]
onehotbatch(target)

# output

10×1×1 Array{Int64, 3}:
[:, :, 1] =
 1
 0
 0
 0
 0
 0
 0
 0
 0
 0
```
