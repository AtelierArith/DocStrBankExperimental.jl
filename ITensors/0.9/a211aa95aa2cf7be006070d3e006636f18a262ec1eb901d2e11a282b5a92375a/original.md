```
directsum(A::Pair{ITensor}, B::Pair{ITensor}, ...; tags)

directsum(output_inds, A::Pair{ITensor}, B::Pair{ITensor}, ...; tags)
```

Given a list of pairs of ITensors and indices, perform a partial direct sum of the tensors over the specified indices. Indices that are not specified to be summed must match between the tensors.

(Note: `Pair{ITensor}` in Julia is short for `Pair{ITensor,<:Any}` which means any pair `T => x` where `T` is an ITensor.)

If all indices are specified then the operation is equivalent to creating a block diagonal tensor.

Returns the ITensor representing the partial direct sum as well as the new direct summed indices. The tags of the direct summed indices are specified by the keyword arguments.

Optionally, pass the new direct summed indices of the output tensor as the first argument (either a single Index or a collection), which must be proper direct sums of the input indices that are specified to be direct summed.

See Section 2.3 of https://arxiv.org/abs/1405.7786 for a definition of a partial direct sum of tensors.

# Examples

```julia
x = Index(2, "x")
i1 = Index(3, "i1")
j1 = Index(4, "j1")
i2 = Index(5, "i2")
j2 = Index(6, "j2")

A1 = random_itensor(x, i1)
A2 = random_itensor(x, i2)
S, s = directsum(A1 => i1, A2 => i2)
dim(s) == dim(i1) + dim(i2)

i1i2 = directsum(i1, i2)
S = directsum(i1i2, A1 => i1, A2 => i2)
hasind(S, i1i2)

A3 = random_itensor(x, j1)
S, s = directsum(A1 => i1, A2 => i2, A3 => j1)
dim(s) == dim(i1) + dim(i2) + dim(j1)

A1 = random_itensor(i1, x, j1)
A2 = random_itensor(x, j2, i2)
S, s = directsum(A1 => (i1, j1), A2 => (i2, j2); tags = ["sum_i", "sum_j"])
length(s) == 2
dim(s[1]) == dim(i1) + dim(i2)
dim(s[2]) == dim(j1) + dim(j2)
```
