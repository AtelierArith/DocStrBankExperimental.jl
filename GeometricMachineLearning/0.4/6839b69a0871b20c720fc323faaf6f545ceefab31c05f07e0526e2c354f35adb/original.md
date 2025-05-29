```
ClassificationLayer(input_dim, output_dim, activation)
```

Make an instance of `ClassificationLayer`.

`ClassificationLayer` takes a matrix as an input and returns a vector that is used for classification. 

It does:

$$
    X \mapsto \sigma(\mathtt{compute\_vector}(AX)),
$$

where $X$ is a matrix and $\mathtt{compute\_vector}$ specifices how this matrix is turned into a vector. 

$\mathtt{compute\_vector}$ can be specified with the keyword `average`.

# Arguments

`ClassificationLayer` has the following optional keyword argument: 

  * `average:Bool=false`.

If this keyword argument is set to `true`, then the output is computed as 

$$
    input \mapsto \frac{1}{N}\sum_{i=1}^N[\mathcal{NN}(input)]_{\bullet{}i}.
$$

If set to `false` (the default) it picks the last column of the input. 

# Examples

```jldoctest
using GeometricMachineLearning

l = ClassificationLayer(2, 2, identity; average = true)
ps = (weight = [1 0; 0 1], )

input = [1 2 3; 1 1 1]

l(input, ps)

# output

2×1 Matrix{Float64}:
 2.0
 1.0
```

```jldoctest
using GeometricMachineLearning

l = ClassificationLayer(2, 2, identity; average = false)
ps = (weight = [1 0; 0 1], )

input = [1 2 3; 1 1 1]

l(input, ps)

# output

2×1 Matrix{Int64}:
 3
 1
```
