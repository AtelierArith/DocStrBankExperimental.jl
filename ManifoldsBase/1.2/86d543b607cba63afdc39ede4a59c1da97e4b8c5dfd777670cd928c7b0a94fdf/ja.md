```
get_coordinates(M::AbstractManifold, p, X, B::AbstractBasis=default_basis(M, typeof(p)))
get_coordinates(M::AbstractManifold, p, X, B::CachedBasis)
```

多様体 `M` 上の点 `p` での接ベクトル `X` の係数の1次元ベクトルを基底 `B` において計算します。

基底によっては、`p` が多様体上の点を直接表さない場合があります。たとえば、曲線に沿って輸送された基底が使用される場合、`p` は曲線に沿った座標である可能性があります。 [`CachedBasis`](@ref) が提供されている場合、その保存されたベクトルが使用されます。そうでない場合、ユーザーは座標を計算する方法を提供する必要があります。

[`CachedBasis`](@ref) に関しては、[`get_vector`](@ref) での再構成には、双対基底またはキャッシュされた基底が自己双対である必要があることに注意してください。たとえば、直交正規です。

関連情報: [`get_vector`](@ref), [`get_basis`](@ref)
