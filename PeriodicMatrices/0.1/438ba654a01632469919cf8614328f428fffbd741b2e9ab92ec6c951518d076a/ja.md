```
 pgschur(A::Array{Float64,3}, s::Union{Vector{Bool},BitVector}; rev = true, withQ = true) -> (S, Z, ev, ischur, α, γ)
```

正方行列の形式的な積 `A(p)^s(p)*...A(2)^s(2)*A(1)^s(1)` の一般化された実周期シュア分解を計算します。`rev = true`（デフォルト）の場合、または `A(1)^s(1)*A(2)^s(2)*...*A(p)^s(p)` の場合、`rev = false` です。ここで 's(j) = ±1' です。行列 `A(1)`, `A(2)`, `...`, `A(p)` は `n×n×p` 配列 `A` に含まれており、`i` 番目の行列 `A(i)` は `A[:,:,i]` に含まれています。

結果として得られる `n×n×p` 配列 `S` には、行列 `S(1)`, `...`, `S(p)` が含まれており、`S(ischur)` は準上三角形の形を持ち、`S(i)` は `i` $\neq$ `ischur` の場合は上三角形です。`withZ = true`（デフォルト）の場合、結果として得られる `n×n×p` 配列 `Z` には直交変換行列 `Z(1)`, `...`, `Z(p)` が含まれます。`withZ = false` の場合、実行された直交変換は蓄積されず、その場合 `Z = nothing` になります。

結果として得られる行列は、`rev = true` の場合に次の条件を満たします。

```
       Z(mod(j,p)+1)' * A(j) * Z(j) = S(j),  もし S[j] = true, 
       Z(j)' * A(j) * Z(mod(j,p)+1) = S(j),  もし S[j] = false,
```

`rev = false` の場合は次の条件を満たします。

```
       Z(j)' * A(j) * Z(mod(j,p)+1) = S(j),  もし S[j] = true, 
       Z(mod(j,p)+1)' * A(j) * Z(j) = S(j),  もし S[j] = false.
```

`S(i)` と `Z(i)` はそれぞれ `S[:,:,i]` と `Z[:,:,i]` に含まれています。ベクトル `ev` には適切な行列積の固有値が含まれています。固有値は `α .* γ` として別の形で表現でき、ここで `γ` は固有値の表現におけるオーバーフローやアンダーフローを避けるための適切なスケーリングパラメータを含みます。

関数 `pgschur` は、SLICOT サブルーチン `MB03VW` （参照 [`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref)）および `MB03BD` （参照 [`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref)）のラッパーに基づいており、[1] および [2] で提案されたアルゴリズムに基づいています。

参考文献

[1] Bojanczyk, A., Golub, G. H. and Van Dooren, P.     The periodic Schur decomposition: algorithms and applications.     In F.T. Luk (editor), Advanced Signal Processing Algorithms,     Architectures, and Implementations III, Proc. SPIE Conference,     vol. 1770, pp. 31-42, 1992.

[2] Kressner, D.     An efficient and reliable implementation of the periodic QZ     algorithm. IFAC Workshop on Periodic Control Systems (PSYCO     2001), Como (Italy), August 27-28 2001. Periodic Control     Systems 2001 (IFAC Proceedings Volumes), Pergamon. ```
