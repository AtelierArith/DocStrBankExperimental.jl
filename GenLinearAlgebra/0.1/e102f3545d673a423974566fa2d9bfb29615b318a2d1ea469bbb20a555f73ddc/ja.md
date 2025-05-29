`bigcell_decomposition(M [, b])`

`M` は正方行列である必要があり、`b` は `M` と同じサイズの行列のブロック構造を指定します（それは `1:size(M,1)` の連結からなる `Vector` の `Vector` です）。`b` が指定されていない場合、トリビアルなブロック構造 `[[i] for i in axes(M,1)]` が仮定されます。

この関数は、`M` を `P₁ L P` の積として分解します。ここで `P` は上部ブロック単位三角行列（単位対角ブロックを持つ）、`P₁` は下部ブロック単位三角行列、`L` はブロック構造 `b` に対してブロック対角行列です。`M` が対称である場合、`P₁` は `P` の転置であり、結果はペア `[P,L]` になります。そうでない場合、結果は三つ組 `[P₁,L,P]` になります。この `M` の分解が可能であるための唯一の条件は、ブロック構造に従った主小行列が可逆であることです。このルーチンは、グリーン関数を計算するためのルスティグ-ショジアルゴリズムで使用され、以下の例は `G₂` のグリーン関数の計算から抽出されています。

```julia-repl
julia> using LaurentPolynomials

julia> @Pol q
Pol{Int64}: q

julia> M=[q^6 q^0 q^3 q^3 q^5+q q^4+q^2; q^0 q^6 q^3 q^3 q^5+q q^4+q^2; q^3 q^3 q^6 q^0 q^4+q^2 q^5+q; q^3 q^3 q^0 q^6 q^4+q^2 q^5+q; q^5+q q^5+q q^4+q^2 q^4+q^2 q^6+q^4+q^2+1 q^5+2*q^3+q; q^4+q^2 q^4+q^2 q^5+q q^5+q q^5+2*q^3+q q^6+q^4+q^2+1]
6×6 Matrix{Pol{Int64}}:
 q⁶     1      q³     q³     q⁵+q        q⁴+q²
 1      q⁶     q³     q³     q⁵+q        q⁴+q²
 q³     q³     q⁶     1      q⁴+q²       q⁵+q
 q³     q³     1      q⁶     q⁴+q²       q⁵+q
 q⁵+q   q⁵+q   q⁴+q²  q⁴+q²  q⁶+q⁴+q²+1  q⁵+2q³+q
 q⁴+q²  q⁴+q²  q⁵+q   q⁵+q   q⁵+2q³+q    q⁶+q⁴+q²+1

julia> bb=[[2],[4],[6],[3,5],[1]];

julia> (P,L)=bigcell_decomposition(M,bb);

julia> P
6×6 Matrix{Pol{Int64}}:
 1    0  0    0    0        0
 q⁻⁶  1  q⁻³  q⁻³  q⁻¹+q⁻⁵  q⁻²+q⁻⁴
 0    0  1    0    0        0
 q⁻³  0  0    1    q⁻²      q⁻¹
 q⁻¹  0  0    0    1        0
 q⁻²  0  q⁻¹  0    q⁻¹      1

julia> L
6×6 Matrix{Pol{Int64}}:
 q⁶-q⁴-1+q⁻²  0   0            0     0            0
 0            q⁶  0            0     0            0
 0            0   q⁶-q⁴-1+q⁻²  0     0            0
 0            0   0            q⁶-1  0            0
 0            0   0            0     q⁶-q⁴-1+q⁻²  0
 0            0   0            0     0            q⁶-1

julia> M==transpose(P)*L*P
true
```
