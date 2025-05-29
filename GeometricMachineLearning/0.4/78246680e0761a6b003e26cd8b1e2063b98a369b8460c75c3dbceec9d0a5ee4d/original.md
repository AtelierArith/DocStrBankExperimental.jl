```
SymmetricMatrix(S::AbstractVector, n::Integer)
```

Instantiate a symmetric matrix with information stored in vector `S`.

A `SymmetricMatrix` $A$ is a matrix $A^T = A$.

Internally the `struct` saves a vector $S$ of size $n(n+1)\div2$. The conversion is done the following way: 

$$
[A]_{ij} = \begin{cases} S[( (i-1) i ) \div 2 + j] & \text{if $i\geq{}j$}\\ 
                         S[( (j-1) j ) \div 2 + i] & \text{else}. \end{cases}
$$

So $S$ stores a string of vectors taken from $A$: $S = [\tilde{a}_1, \tilde{a}_2, \ldots, \tilde{a}_n]$ with $\tilde{a}_i = [[A]_{i1},[A]_{i2},\ldots,[A]_{ii}]$.

Also see [`SkewSymMatrix`](@ref), [`LowerTriangular`](@ref) and [`UpperTriangular`](@ref).

# Examples

```jldoctest
using GeometricMachineLearning
S = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
SymmetricMatrix(S, 4)

# output

4×4 SymmetricMatrix{Int64, Vector{Int64}}:
 1  2  4   7
 2  3  5   8
 4  5  6   9
 7  8  9  10
```
