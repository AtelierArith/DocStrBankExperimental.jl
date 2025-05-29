```
 hr2btupd(Ahr::HarmonicArray, N; P, nperiod, shift]) -> Ab::Matrix
```

Build the updated block Toeplitz matrix of a harmonic (Fourier) array representation of a periodic matrix. 

If `BT` is the block Toeplitz matrix of the harmonic array representation of the `n × n` periodic matrix `Ahr` of subperiod `T′`  (see [`HarmonicArray`](@ref)) as constructed with [`hr2bt`](@ref), then the updated matrix Ab = BT-NT is constructed,  with `NT` a block-diagonal matrix with `n × n` diagonal blocks. The `k`-th diagonal block of `NT` is the diagonal matrix `im*(μ + k*ωh)*I`, where `μ` is a shift specified via  the keyword parameter `shift = μ` (default: `μ = 0`)  and `ωh` is the base frequency computed as `ωh = 2π*nperiod/(P*T′)`.  The value of shift must satisfy `0 ≤ μ ≤ ωh/2`. 
