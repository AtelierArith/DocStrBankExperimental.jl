```
prank(M::AbstractMatrix, N::AbstractMatrix; fastrank = true, atol1::Real=0, atol2::Real=0, rtol::Real=min(atol1,atol2)>0 ? 0 : n*ϵ)
```

行列ペンシル `M - λN` の通常のランクを計算します。`fastrank = true` の場合、ランクは `M - γ N` の特異値のうち、絶対値が `max(max(atol1,atol2), rtol*σ₁)` より大きいものの数を数えることによって評価されます。ここで、`σ₁` は `M - γ N` の最大特異値であり、`γ` はランダムに生成された値です。`fastrank = false` の場合、ランクは `nr + ni + nf + nl` として評価されます。ここで、`nr` と `nl` はそれぞれ右および左のクロンカー指数の合計であり、`ni` と `nf` はそれぞれ無限および有限の固有値の数です。合計 `nr+ni` と `nf+nl` は、ペンシル `M - λN` の右および左の構造の分割を示す適切なクロンカー様形式 (KLF) から決定されます。

キーワード引数 `atol1`、`atol2`、および `rtol` は、それぞれ `M` の非ゼロ要素の絶対許容誤差、`N` の非ゼロ要素の絶対許容誤差、および `M` と `N` の非ゼロ要素の相対許容誤差を指定します。デフォルトの相対許容誤差は `n*ϵ` であり、ここで `n` は `M` の最小次元のサイズで、`ϵ` は `M` の要素型のマシンイプシロンです。効率のために、関連する KLF への削減は、ランクを明らかにする SVD 分解に基づくランク決定を使用して部分的にのみ実行されます。

!!! compat "Julia 1.1"
    ランク決定における `atol` および `rtol` キーワード引数の使用は、少なくとも Julia 1.1 を必要とします。Julia 1.0 との互換性を強制するために、Julia 1.1 の新しい関数 rank が明示的に含まれています。


```
