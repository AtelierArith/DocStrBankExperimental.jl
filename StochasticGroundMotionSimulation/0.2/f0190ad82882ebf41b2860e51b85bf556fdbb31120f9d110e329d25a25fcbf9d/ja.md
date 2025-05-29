```
create_spectral_moments(order::Vector{Int}, value::Vector{T}) where {T<:Real}
```

整数の順序とモーメント値のベクトルから `SpectralMoments` インスタンスを作成します。返されるインスタンス内で名前付きモーメントをカプセル化することができます。
