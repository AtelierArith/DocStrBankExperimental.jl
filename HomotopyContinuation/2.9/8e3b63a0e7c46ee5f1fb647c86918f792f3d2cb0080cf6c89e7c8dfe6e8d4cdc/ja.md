```
permutations(r::MonodromyResult; reduced=true)
```

ループを追跡することによって誘導される解の順列を返します。`reduced=false` の場合、すべての順列が返されます。`reduced=true` の場合、重複のない順列が返されます。

解がループで追跡されなかった場合、対応するエントリは 0 になります。

例: 2つの円と交差する変化する直線のモノドロミーループ。

```julia
using LinearAlgebra
@var x[1:2] a b c
c1 = (x - [2, 0]) ⋅ (x - [2, 0]) - 1
c2 = (x - [-2, 0]) ⋅ (x - [-2, 0]) - 1
F = [c1 * c2; a * x[1] + b * x[2] - c]
S = monodromy_solve(F, [[1, 0]], [1, 1, 1], parameters = [a, b, c], permutations = true)

permutations(S)
```

は次のように返します。

```julia
2×2 Array{Int64,2}:
 1  2
 2  1
```

そして `permutations(S, reduced = false)` は次のように返します。

```julia
2×12 Array{Int64,2}:
 1  2  2  1  1  …  1  2  1  1  1
 2  1  1  2  2     2  1  2  2  2
```
