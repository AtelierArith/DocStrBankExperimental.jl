```
 pschur(A::Vector{Matrix{T}}, E::Vector{Matrix{T}}; rev = true, withZ = true) -> (S, T, Q, Z, ev, ischur, α, γ)
```

行列の平方形式の積 `inv(E(p))*A(p)*...*inv(E(2))*A(2)*inv(E(1))*A(1)` の拡張周期シュア分解を計算します。`rev = true`（デフォルト）の場合、または `A(1)*inv(E(1))*A(2)*inv(E(2))*...*A(p)*inv(E(p))` の場合は `rev = false` です。積と逆行列を評価することなく計算します。行列 `A(1)`, `...`, `A(p)` は、`A` の `p` ベクトルに含まれており、`i` 番目の行列 `A(i)` は `m(i)×n(i)` の次元を持ち、`A[i]` に含まれています。平方行列 `E(1)`, `...`, `E(p)` は、`E` の `p` ベクトルに含まれており、`i` 番目の行列 `E(i)` は、`rev = true` の場合は `m(i)×m(i)` の次元を持ち、`rev = false` の場合は `n(i)×n(i)` の次元を持ち、`E[i]` に含まれています。

結果のインデックス `ischur` は、`m(ischur) ≤ m(i), ∀i` となるように決定されます。結果の `p` ベクトル `S`, `T`, `Q` および `Z` は、それぞれ、行列 `S(1)`, `...`, `S(p)` を含み、`S(ischur)` は準上三角台形の形を持ち、`S(i)` は `i` $\neq$ `ischur` の場合は上三角台形です。上三角行列 `T(1)`, `...`, `T(p)`、直交行列 `Q(1)`, `...`, `Q(p)`、および `Z(1)`, `...`, `Z(p)` が含まれています。`rev = true` の場合は次のようになります。

```
       Q(1)' * A(1) * Z(1) = S(1),  Q(1)' * E(1) * Z(2) = T(1), 
       Q(2)' * A(2) * Z(2) = S(2),  Q(2)' * E(2) * Z(3) = T(2),
              ...
       Q(p)' * A(p) * Z(p) = S(p),  Q(p)' * E(p) * Z(1) = T(p),
```

`rev = false` の場合は次のようになります。

```
       Q(1)' * A(1) * Z(1) = S(1),  Q(2)' * E(1) * Z(1) = T(1), 
       Q(2)' * A(2) * Z(2) = S(2),  Q(3)' * E(2) * Z(2) = T(2),
              ...
       Q(p)' * A(p) * Z(p) = S(p),  Q(1)' * E(p) * Z(p) = T(p),
```

`ev := α .* γ` の最初の `nmin` 成分は、適切な行列積の *コア固有値* を含み、ここで `nmin = m(ischur)` です。一方、`ev` の最後の `nmax-nmin` 成分はゼロです。ここで `nmax` は `A(i)` の最大の行または列の次元であり、`i = 1, ..., p` の範囲です。固有値は `α .* γ` としても表現でき、`γ` は固有値の表現におけるオーバーフローやアンダーフローを避けるための適切なスケーリングパラメータを含みます。`withZ = false` の場合、実行された直交変換は蓄積されず、その場合 `Q = nothing` および `Z = nothing` となります。

関数 `pschur` は、SLICOT サブルーチン `MB03VW`（[`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref) を参照）および `MB03BD`（[`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref) を参照）のラッパーに基づいており、[1] および [2] で提案されたアルゴリズムに基づいています。

REFERENCES

[1] Bojanczyk, A., Golub, G. H. and Van Dooren, P.     The periodic Schur decomposition: algorithms and applications.     In F.T. Luk (editor), Advanced Signal Processing Algorithms,     Architectures, and Implementations III, Proc. SPIE Conference,     vol. 1770, pp. 31-42, 1992.

[2] Kressner, D.     An efficient and reliable implementation of the periodic QZ     algorithm. IFAC Workshop on Periodic Control Systems (PSYCO     2001), Como (Italy), August 27-28 2001. Periodic Control     Systems 2001 (IFAC Proceedings Volumes), Pergamon.
