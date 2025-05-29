```
SkewSymMatrix(S::AbstractVector, n::Integer)
```

Instantiate a skew-symmetric matrix with information stored in vector `S`.

A skew-symmetric matrix $A$ is a matrix $A^T = -A$.

Internally the `struct` saves a vector $S$ of size $n(n-1)\div2$. The conversion is done the following way: 

$$
[A]_{ij} = \begin{cases} 0                             & \text{if $i=j$} \\
                         S[( (i-2) (i-1) ) \div 2 + j] & \text{if $i>j$}\\ 
                         S[( (j-2) (j-1) ) \div 2 + i] & \text{else}. \end{cases}
$$

So $S$ stores a string of vectors taken from $A$: $S = [\tilde{a}_1, \tilde{a}_2, \ldots, \tilde{a}_n]$ with $\tilde{a}_i = [[A]_{i1},[A]_{i2},\ldots,[A]_{i(i-1)}]$.

Also see [`SymmetricMatrix`](@ref), [`LowerTriangular`](@ref) and [`UpperTriangular`](@ref).

# Examples

```jldoctest
using GeometricMachineLearning
S = [1, 2, 3, 4, 5, 6]
SkewSymMatrix(S, 4)

# output

4×4 SkewSymMatrix{Int64, Vector{Int64}}:
 0  -1  -2  -4
 1   0  -3  -5
 2   3   0  -6
 4   5   6   0
```
