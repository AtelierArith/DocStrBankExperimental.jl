`word(b::GarsideElt)`

は、`b` の説明を、その積である原子のリストとして返します。`b` がガーサイド群に属するがガーサイドモノイドには属さない場合、特別な規約として、原子の逆元は対応する整数を negating することで表現され、分数標準形で表されます。

```julia-repl
julia> B=BraidMonoid(coxgroup(:A,3))
BraidMonoid(A₃)

julia> b=B(2,1,2,1,1)*inv(B(2,2))
(21)⁻¹1.12.21

julia> word(b)
7-element Vector{Int64}:
 -1
 -2
  1
  1
  2
  2
  1
```
