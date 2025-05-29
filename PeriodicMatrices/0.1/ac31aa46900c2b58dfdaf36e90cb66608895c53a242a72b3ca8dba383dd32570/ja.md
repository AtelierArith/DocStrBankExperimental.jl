```
 pschur(A::AbstractArray{T,3}, E::AbstractArray{T,3}; rev = true, withZ = true) -> (S, T, Q, Z, ev, ischur, α, γ)
```

行列の正方形形式の商積 `inv(E(p))*A(p)*...*inv(E(2))*A(2)*inv(E(1))*A(1)` の周期的シュア分解を計算します。`rev = true`（デフォルト）であれば、または `A(1)*inv(E(1))*A(2)*inv(E(2))*...*A(p)*inv(E(p))` であれば `rev = false` の場合、積と逆行列を評価することなく計算します。行列 `A(1)`, `...`, `A(p)` は `n×n×p` 配列 `A` に含まれており、`i` 番目の行列 `A(i)` は `A[:,:,i]` に含まれています。正方行列 `E(1)`, `...`, `E(p)` は `n×n×p` 配列 `E` に含まれており、`i` 番目の行列 `E(i)` は `E[:,:,i]` に含まれています。

結果として得られる `n×n×p` 配列 `S`, `T`, `Q` および `Z` は、それぞれ、行列 `S(1)`, `...`, `S(p)` を含み、`S(ischur)` は準上三角台形形式であり、`S(i)` は `i` $\neq$ `ischur` の場合は上三角台形です。上三角行列 `T(1)`, `...`, `T(p)`、直交行列 `Q(1)`, `...`, `Q(p)`、および `Z(1)`, `...`, `Z(p)` が含まれ、`rev = true` の場合は次のようになります。

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

複素ベクトル `ev` は適切な行列積の固有値を含み、`ev := α .* γ` として別の形で表現できます。ここで `γ` は固有値の表現におけるオーバーフローやアンダーフローを避けるための適切なスケーリングパラメータを含みます。実行された直交変換は `withZ = false` の場合には蓄積されず、その場合 `Q = nothing` および `Z = nothing` となります。

関数 `pschur` は SLICOT サブルーチン `MB03VW`（[`PeriodicMatrices.SLICOTtools.mb03vw!`](@ref) を参照）および `MB03BD`（[`PeriodicMatrices.SLICOTtools.mb03bd!`](@ref) を参照）用のラッパーに基づいており、[1] および [2] で提案されたアルゴリズムに基づいています。

REFERENCES

[1] Bojanczyk, A., Golub, G. H. and Van Dooren, P.     The periodic Schur decomposition: algorithms and applications.     In F.T. Luk (editor), Advanced Signal Processing Algorithms,     Architectures, and Implementations III, Proc. SPIE Conference,     vol. 1770, pp. 31-42, 1992.

[2] Kressner, D.     An efficient and reliable implementation of the periodic QZ     algorithm. IFAC Workshop on Periodic Control Systems (PSYCO     2001), Como (Italy), August 27-28 2001. Periodic Control     Systems 2001 (IFAC Proceedings Volumes), Pergamon. ```
