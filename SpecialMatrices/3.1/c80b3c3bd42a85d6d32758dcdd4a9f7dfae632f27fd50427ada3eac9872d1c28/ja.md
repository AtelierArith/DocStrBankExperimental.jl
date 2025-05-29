```
Riemann(N::Int)
```

`N × N` の `Riemann` 行列を構築します。これは `A = B[2:N+1, 2:N+1]` と定義され、`B[i,j] = i-1` もし `i` が `j` を割り切る場合、そうでなければ `-1` です。 [リーマン予想](https://en.wikipedia.org/wiki/Riemann_hypothesis) は、`det(A) = O(N! N^(-1/2+ϵ))` がすべての `ϵ > 0` に対して成り立つ場合に限り成立します。

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

詳細については、Friedrich Roesler の "Riemann's hypothesis as an eigenvalue problem," Linear Algebra and its Applications, Vol. 81, p.153-198, Sep. 1986 を参照してください。 https://doi.org/10.1016/0024-3795(86)90255-7
