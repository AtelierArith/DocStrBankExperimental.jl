```
 pschur(A::Vector{Matrix{T}}; rev = true, withZ = true) -> (S, Z, ev, ischur, α, γ)
 pschur1(A::Vector{Matrix{T}}; rev = true, withZ = true) -> (S, Z, ev, ischur, α, γ)
```

行列の平方積 `A(p)*...*A(2)*A(1)` の拡張周期シュア分解を計算します。`rev = true`（デフォルト）の場合、または `A(1)*A(2)*...*A(p)` の場合は `rev = false` で、積を評価することなく行います。行列 `A(1)`, `...`, `A(p)` は、`i` 番目の行列 `A(i)` が `A[i]` に含まれるように、行列の `p` ベクトルに含まれています。結果として得られる `p` ベクトル `S` と `Z` には、それぞれ行列 `S(1)`, `...`, `S(p)` と直交行列 `Z(1)`, `...`, `Z(p)` が含まれ、`rev = true` の場合は次のようになります。

```
       Z(2)' * A(1) * Z(1) = S(1),
       Z(3)' * A(2) * Z(2) = S(2),
              ...
       Z(1)' * A(p) * Z(p) = S(p),
```

`rev = false` の場合は次のようになります。

```
       Z(1)' * A(1) * Z(2) = S(1),
       Z(2)' * A(2) * Z(3) = S(2),
              ...
       Z(p)' * A(p) * Z(1) = S(p).
```

結果のインデックス `ischur` は `m(ischur) ≤ m(i), ∀i` となるように決定されます。`i = 1, ..., p` の `S(i)` は拡張周期シュア形式にあり、`S(ischur)` は準上三角台形形式で、`S(i)` は `i` $\neq$ `ischur` の場合は上三角台形です。`S(i)` と `Z(i)` はそれぞれ `S[i]` と `Z[i]` に含まれます。`ev := α .* γ` の最初の `nmin` 成分は、適切な行列積の*コア固有値*を含み、ここで `nmin = m(ischur)` です。一方、`ev` の最後の `nmax-nmin` 成分はゼロであり、`nmax` は `i = 1, ..., p` の `A(i)` の最大行または列の次元です。固有値は `α .* γ` としても表現でき、ここで `γ` は固有値の表現におけるオーバーフローやアンダーフローを避けるための適切なスケーリングパラメータを含みます。`withZ = false` の場合、実行された直交変換は蓄積されず、その場合 `Z = nothing` となります。

関数 `pschur` は、SLICOT サブルーチン `MB03VW` のラッパーに基づいており（[`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref) を参照）、および `MB03BD`（[`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref) を参照）に基づいており、[1] および [2] で提案されたアルゴリズムに基づいています。

関数 `pschur1` は、SLICOT サブルーチン `MB03VD`（[`PeriodicMatrices.SLICOTtools.mb03vd!`](@ref) を参照）、`MB03VY`（[`PeriodicMatrices.SLICOTtools.mb03vy!`](@ref) を参照）、および `MB03BD`（[`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref) を参照）のラッパーに基づいており、[1] および [2] で提案されたアルゴリズムに基づいています。

参考文献

[1] Bojanczyk, A., Golub, G. H. and Van Dooren, P.     The periodic Schur decomposition: algorithms and applications.     In F.T. Luk (editor), Advanced Signal Processing Algorithms,     Architectures, and Implementations III, Proc. SPIE Conference,     vol. 1770, pp. 31-42, 1992.

[2] Kressner, D.     An efficient and reliable implementation of the periodic QZ     algorithm. IFAC Workshop on Periodic Control Systems (PSYCO     2001), Como (Italy), August 27-28 2001. Periodic Control     Systems 2001 (IFAC Proceedings Volumes), Pergamon.
