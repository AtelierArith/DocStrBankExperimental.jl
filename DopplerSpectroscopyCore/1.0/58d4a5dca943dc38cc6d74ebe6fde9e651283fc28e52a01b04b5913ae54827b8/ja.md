```
probe(δ::Real, two_level, light) -> Real
probe(δ_vec::Vector{T}, two_level, light) -> Vector{T} where T<:Real
probe(δ_range::LinRange{T1, T2}, two_level, light)
-> Vector{T1} where {T1<:Real, T2<:Integer}
```

量子系が励起状態にある確率 `nₑ` を、デチューニング `δ` に対して計算します。複数のデチューニング値を `δ_vec` または `δ_range` を介して供給することで、それぞれの値に対して `nₑ` を計算します。

# 引数

  * `δ` :
  * `two_level::Quantum2Level` :
  * `light::LightSource` :

# 戻り値

  * `nₑ` :   実数。

# 参照

  * [`StateVector`](@ref)

# 参考文献

  * Springer: https://link.springer.com/chapter/10.1007/978-1-4684-4550-3_5   (もし無償でアクセスできる参考文献を見つけた場合は、パッケージの GitHub ページに記載されているメールアドレスに連絡するか、問題を作成してください)
