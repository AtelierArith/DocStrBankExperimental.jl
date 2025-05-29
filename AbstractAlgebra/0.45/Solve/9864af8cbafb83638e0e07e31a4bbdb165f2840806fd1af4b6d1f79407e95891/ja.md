```
solve_init(A::MatElem)
```

異なる $b$ に対して線形システム $Ax = b$ または $xA = b$ を効率的に解くためのコンテキストオブジェクト `C` を返します。

# 例

```jldoctest
julia> A = QQ[1 2 3; 0 3 0; 5 0 0];

julia> C = solve_init(A)
行列の線形解決コンテキスト
  [1//1   2//1   3//1]
  [0//1   3//1   0//1]
  [5//1   0//1   0//1]

julia> solve(C, [QQ(1), QQ(1), QQ(1)]; side = :left)
3-element Vector{Rational{BigInt}}:
 1//3
 1//9
 2//15

julia> solve(C, [QQ(1), QQ(1), QQ(1)]; side = :right)
3-element Vector{Rational{BigInt}}:
 1//5
 1//3
 2//45
```
