```
SymmetricEmbedding(ste::SpatioTemporalEmbedding, sym::Tuple)
```

`SymmetricEmbedding`は、システム内の空間対称性を利用して[`SpatioTemporalEmbedding`](@ref)の次元削減を目的としています。これは、すべての可能な対称性の`<:Symmetry`の`Tuple`としてリストされます（詳細は[`Symmetry`](@ref）を参照）。

`sym`で渡された対称性に従って、時間ステップで互いに等しいすべての点は**平均化**されて単一のエントリになります！例えば、対称性`Reflection(2)`は、埋め込みが2つのエントリ`u[i, j+1], u[i, j-1]`を持たず、代わりに単一のエントリ`(u[i, j+1] + u[i, j-1])/2`を持つことを意味します。ここで、`i,j`は埋め込みの中心点に対するインデックスです。（このプロセスは、空間半径`r`がどれだけ大きいかに応じて、任意のインデックスオフセット`j+2, j+3`などについても行われます）

`SymmetricEmbedding`から得られる構造は、[`SpatioTemporalEmbedding`](@ref)と同様にデータセットを再構築するために使用できます。
