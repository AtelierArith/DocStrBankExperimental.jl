```
calculateToeplitzKernel!(f::Array{Complex{T}}, p::AbstractNFFTPlan, tr::Matrix{T}, fftplan)
```

トープリッツ構造を利用したグラム行列の実装のためのカーネルを計算し、`f`にインプレースで書き込みます。`f`は、トープリッツトリックが2のオーバーサンプリングファクターを必要とするため、希望する画像行列の2倍のサイズでなければなりません（cf. [Wajer, F. T. A. W., and K. P. Pruessmann. "Major speedup of reconstruction for sensitivity encoding with arbitrary trajectories." Proc. Intl. Soc. Mag. Res. Med. 2001.](https://cds.ismrm.org/ismrm-2001/PDF3/0767.pdf)）。カーネル`f`の型は`Complex{T}`でなければならず、すなわちk空間の軌道の型の複素数です。速度とメモリ効率のために、この関数を`Float32.(tr)`で呼び出し、`f`の型をそれに応じて設定してください。

# 必要な引数

  * `f::Array{T}`: カーネルが書き込まれる配列。
  * `p::AbstractNFFTPlan`: `tr`と同じ次元のNFFTPlanで、インプレースで上書きされます。
  * `tr::Matrix{T}`: 非カルテジアンk空間軌道で、単位は回転/ボクセルです。すなわち、`tr[i] ∈ [-0.5, 0.5] ∀ i`。行列は、2Dイメージングの場合は`2 x Nsamples`のサイズを持ち、軌道の長さは`Nsamples`、3Dイメージングの場合は`3 x Nsamples`のサイズを持ちます。
  * `fftplan`: 画像からk空間へのカーネルの最終FFTのためのプランです。したがって、元の画像の2倍のサイズでなければなりません。例えば、`fftplan = plan_fft(zeros(Complex{T}, 2 .* shape); flags=FFTW.MEASURE)`で計算します。ここで、`shape`は再構成された画像のサイズです。

# 例

```jldoctest; output = false, setup = :(using NFFT, NFFTTools, Random; Random.seed!(1))
julia> using FFTW

julia> Nx = 32;

julia> trj = Float32.(rand(2, 1000) .- 0.5);

julia> p = plan_nfft(trj, (2Nx,2Nx))
NFFTPlan with 1000 sampling points for an input array of size(64, 64) and an output array of size(1000,) with dims 1:2

julia> fftplan = plan_fft(zeros(ComplexF32, (2Nx,2Nx)); flags=FFTW.MEASURE);

julia> λ = Array{ComplexF32}(undef, 2Nx, 2Nx);

julia> calculateToeplitzKernel!(λ, p, trj, fftplan);

julia> y = randn(ComplexF32, Nx, Nx);

julia> convolveToeplitzKernel!(y, λ);

```
