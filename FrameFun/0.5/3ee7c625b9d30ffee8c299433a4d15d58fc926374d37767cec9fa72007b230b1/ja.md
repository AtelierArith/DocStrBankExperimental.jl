```
extensionframe(basis::Dictionary, domain::Domain)

extensionframe(domain::Domain, basis::Dictionary)
```

拡張フレームを作成しますが、テンソル積ドメインを適切な方法でテンソル積集合と一致させます。

# 例

例えば：区間 ⊗ ディスク（＝円柱）を3Dフーリエ級数と組み合わせると、区間上のフーリエ級数 ⊗ ディスク上の2Dフーリエ級数のテンソル積が得られます。

```jldocs
julia> extensionframe(Fourier(10)^2,Disk(.4, SVector(0.5,0.5)))
Dictionary 𝔼(F ⊗ F)

𝔼   :   拡張フレーム、2次元単位球に基づいてマッピングされたドメインから0.0..1.0（単位）×0.0..1.0（単位）への
F   :   フーリエ級数
            ↳ 長さ = 10
            ↳ Float64 -> Complex{Float64}
            ↳ サポート = 0.0..1.0（単位）


julia> extensionframe(Fourier(10)^2,(0.0..0.5)^2)
Dictionary 𝔼(F) ⊗ 𝔼(F)

𝔼   :   拡張フレーム、0.0..0.5から0.0..1.0（単位）への
F   :   フーリエ級数
            ↳ 長さ = 10
            ↳ Float64 -> Complex{Float64}
            ↳ サポート = 0.0..1.0（単位）

```
