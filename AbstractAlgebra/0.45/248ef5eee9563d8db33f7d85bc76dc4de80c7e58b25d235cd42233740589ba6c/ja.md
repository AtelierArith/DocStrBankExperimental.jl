```
similarity!(A::MatrixElem{T}, r::Int, d::T) where {T <: RingElement}
```

$$
n \times n
$$

行列 $M$ に対して、類似変換をインプレースで適用します。$P$ を $n \times n$ 単位行列とし、行 $r$ のすべてのゼロエントリを $d$ に置き換えたものとすると、適用される変換は $M = P^{-1}MP$ に相当します。$M$ は正方行列である必要があります。類似変換は行列の最小多項式と特性多項式を保持します。

# 例

```jldoctest
julia> R, = residue_ring(ZZ, 7);

julia> S = matrix_space(R, 4, 4)
Matrix space of 4 rows and 4 columns
  over residue ring of integers modulo 7

julia> M = S([R(1) R(2) R(4) R(3); R(2) R(5) R(1) R(0);
              R(6) R(1) R(3) R(2); R(1) R(1) R(3) R(5)])
[1   2   4   3]
[2   5   1   0]
[6   1   3   2]
[1   1   3   5]

julia> similarity!(M, 1, R(3))

```
