```
transform(op::SymOperation, P::AbstractMatrix{<:Real}, 
          p::Union{AbstractVector{<:Real}, Nothing}=nothing,
          modw::Bool=true)                           --> SymOperation
```

`op` $= {\mathbf{W}|\mathbf{w}} を回転行列 `P` と平行移動ベクトル `p`（ゼロ平行移動の場合は `nothing` も可）によって変換し、新しい対称操作 `op′` $= {\mathbf{W}'|\mathbf{w}'} を生成します（[^\ITA6]のセクション1.5.2.3を参照）。

$$
\{\mathbf{W}'|\mathbf{w}'\} = \{\mathbf{P}|\mathbf{p}\}^{-1}\{\mathbf{W}|\mathbf{w}\}
\{\mathbf{P}|\mathbf{p}\}
$$

ここで

$$
\mathbf{W}' = \mathbf{P}^{-1}\mathbf{W}\mathbf{P}
\text{ および }
\mathbf{w}' = \mathbf{P}^{-1}(\mathbf{w}+\mathbf{W}\mathbf{p}-\mathbf{p})
$$

デフォルトでは、`op′` の平行移動部分、すなわち $\mathbf{w}'$ は範囲 $[0,1)$ に制限され、すなわち 1 で計算されます。これは `modw = false` に設定することで無効にできます（デフォルトは `modw = true`）。

また、[`Bravais.primitivize(::SymOperation, ::Char, ::Bool)`](@ref) および [`Bravais.conventionalize(::SymOperation, ::Char, ::Bool)`](@ref) も参照してください。

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th ed. (2016).
