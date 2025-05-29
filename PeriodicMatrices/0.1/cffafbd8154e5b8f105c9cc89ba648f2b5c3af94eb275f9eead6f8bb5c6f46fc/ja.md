```
 pschur(A::Array{Float64,3}; rev = true, withZ = true) -> (S, Z, ev, ischur, α, γ)
 pschur1(A::Array{Float64,3}; rev = true, withZ = true) -> (S, Z, ev, ischur, α, γ)
 pschur2(A::Array{Float64,3}; rev = true, withZ = true) -> (S, Z, ev, ischur, α, γ)
```

正方行列の積 `A(p)*...*A(2)*A(1)` のシュア分解を計算します。`rev = true`（デフォルト）であれば、または `A(1)*A(2)*...*A(p)` の場合は `rev = false` で、積を評価することなく行います。行列 `A(1)`, `...`, `A(p)` は `n×n×p` 配列 `A` に含まれており、`i` 番目の行列 `A(i)` は `A[:,:,i]` に含まれています。結果として得られる `n×n×p` 配列 `S` と `Z` には、それぞれ行列 `S(1)`, `...`, `S(p)` と直交行列 `Z(1)`, `...`, `Z(p)` が含まれ、`rev = true` の場合は次のようになります。

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

`sind = ischur` の場合、`1 ≤ ischur ≤ p`（デフォルト `ischur = 1`）で、`S(i)` は周期的シュア形式にあり、`S(ischur)` は準上三角（またはシュア）形式で、`S(i)` は `i` $\neq$ `ischur` の場合は上三角です。`S(i)` と `Z(i)` はそれぞれ `S[:,:,i]` と `Z[:,:,i]` に含まれています。ベクトル `ev` には適切な行列積の固有値が含まれています。固有値は `α .* γ` として別の形で表現でき、`γ` には固有値の表現におけるオーバーフローやアンダーフローを避けるための適切なスケーリングパラメータが含まれています。`withZ = false` の場合、実行された直交変換は蓄積されず、その場合 `Z = nothing` となります。

関数 `pschur` は SLICOT サブルーチン `MB03VW` のラッパーに基づいており（[`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref) を参照）、`MB03BD` に基づいています（[`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref) を参照）。これは [1] および [2] で提案されたアルゴリズムに基づいています。

関数 `pschur1` は SLICOT サブルーチン `MB03VD` のラッパーに基づいており（[`PeriodicMatrices.SLICOTtools.mb03vd!`](@ref) を参照）、`MB03VY`（[`PeriodicMatrices.SLICOTtools.mb03vy!`](@ref) を参照）および `MB03BD`（[`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref) を参照）に基づいています。これも [1] および [2] で提案されたアルゴリズムに基づいています。

関数 `pschur2` は SLICOT サブルーチン `MB03VD` のラッパーに基づいており（[`PeriodicMatrices.SLICOTtools.mb03vd!`](@ref) を参照）、`MB03VY`（[`PeriodicMatrices.SLICOTtools.mb03vy!`](@ref) を参照）および `MB03VW`（[`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref) を参照）に基づいています。これは [1] で提案されたアルゴリズムに基づいています。既知の問題：`MB03VW` は大きな周期に対して失敗する可能性があります。

REFERENCES

[1] Bojanczyk, A., Golub, G. H. and Van Dooren, P.     The periodic Schur decomposition: algorithms and applications.     In F.T. Luk (editor), Advanced Signal Processing Algorithms,     Architectures, and Implementations III, Proc. SPIE Conference,     vol. 1770, pp. 31-42, 1992.

[2] Kressner, D.     An efficient and reliable implementation of the periodic QZ     algorithm. IFAC Workshop on Periodic Control Systems (PSYCO     2001), Como (Italy), August 27-28 2001. Periodic Control     Systems 2001 (IFAC Proceedings Volumes), Pergamon. ```
