```
extensionframe(basis::Dictionary, domain::Domain)

extensionframe(domain::Domain, basis::Dictionary)
```

Make an ExtensionFrame, but match tensor product domains with tensor product sets in a suitable way.

# examples

For example: an interval ⊗ a disk (= a cylinder) combined with a 3D Fourier series, leads to a tensor product of a Fourier series on the interval ⊗ a 2D Fourier series on the disk.

```jldocs
julia> extensionframe(Fourier(10)^2,Disk(.4, SVector(0.5,0.5)))
Dictionary 𝔼(F ⊗ F)

𝔼   :   Extension frame, from A mapped domain based on the 2-dimensional unit ball to 0.0..1.0 (Unit) x 0.0..1.0 (Unit)
F   :   Fourier series
            ↳ length = 10
            ↳ Float64 -> Complex{Float64}
            ↳ support = 0.0..1.0 (Unit)


julia> extensionframe(Fourier(10)^2,(0.0..0.5)^2)
Dictionary 𝔼(F) ⊗ 𝔼(F)

𝔼   :   Extension frame, from 0.0..0.5 to 0.0..1.0 (Unit)
F   :   Fourier series
            ↳ length = 10
            ↳ Float64 -> Complex{Float64}
            ↳ support = 0.0..1.0 (Unit)

```
