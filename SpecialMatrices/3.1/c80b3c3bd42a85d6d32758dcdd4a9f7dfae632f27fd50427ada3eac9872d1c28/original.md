```
Riemann(N::Int)
```

Construct `N × N` `Riemann` matrix, defined as `A = B[2:N+1, 2:N+1]`, where `B[i,j] = i-1` if `i` divides `j`, and `-1` otherwise. The [Riemann hypothesis](https://en.wikipedia.org/wiki/Riemann_hypothesis) holds if and only if `det(A) = O(N! N^(-1/2+ϵ))` for every `ϵ > 0`.

```jldoctest
julia> Riemann(7)
7×7 Riemann{Int64}:
  1  -1   1  -1   1  -1   1
 -1   2  -1  -1   2  -1  -1
 -1  -1   3  -1  -1  -1   3
 -1  -1  -1   4  -1  -1  -1
 -1  -1  -1  -1   5  -1  -1
 -1  -1  -1  -1  -1   6  -1
 -1  -1  -1  -1  -1  -1   7
```

For more details see Friedrich Roesler, "Riemann's hypothesis as an eigenvalue problem," Linear Algebra and its Applications, Vol. 81, p.153-198, Sep. 1986. https://doi.org/10.1016/0024-3795(86)90255-7
