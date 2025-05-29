```
X = get_vector(M::AbstractManifold, p, c, B::AbstractBasis=default_basis(M, typeof(p)))
```

多様体 `M` の点 `p` における接空間の基底 `B` の係数の一次元ベクトルを、点 `p` における接ベクトル `X` に変換します。

基底によっては、`p` が多様体上の点を直接表さない場合があります。たとえば、曲線に沿って輸送された基底が使用される場合、`p` は曲線に沿った座標である可能性があります。

[`CachedBasis`](@ref) に関しては、[`get_coordinates`](@ref) からの再構築には、双対基底またはキャッシュされた基底が自己双対である必要があることに注意してください。たとえば、直交正規です。

関連情報: [`get_coordinates`](@ref), [`get_basis`](@ref), [`default_basis`](@ref)
