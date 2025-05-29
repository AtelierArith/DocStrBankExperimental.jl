```
convolveToeplitzKernel!(y::Array{T,N}, λ::Array{T,N}[, fftplan = plan_fft(λ; flags=FFTW.ESTIMATE), ifftplan = plan_ifft(λ; flags=FFTW.ESTIMATE), xOS1 = similar(λ), xOS2 = similar(λ)])
```

画像 `y` をトプリッツカーネル `λ` で畳み込み、結果で `y` を上書きします。便利のために `y` も返されます。この関数は多くの回数適用されることが一般的なので、すべてのオプション引数を事前に割り当て/計算することを強く推奨します。そうすることで、この関数全体は非割り当てになります。

# 必須引数

  * `y::Array{T,N}`: 結果で上書きされる入力画像。`y` は2Dイメージングの場合は行列（`N=2`）、3Dイメージングの場合は3Dテンソル（`N=3`）です。要素の型 `T` は `λ` のものと一致する必要があります。
  * `λ::Array{T,N}`: トプリッツカーネルで、`k` と同じ型でなければなりませんが、必要なオーバーサンプリングのために2倍のサイズである必要があります（cf. [`calculateToeplitzKernel`](@ref)）。

# オプションですが強く推奨される引数

  * `fftplan`: オーバーサンプリングされたFFTの計画、すなわち元の画像の2倍のサイズでなければなりません。例えば、`fftplan = plan_fft(λ; flags=FFTW.MEASURE)` で計算します。ここで `shape` は再構成された画像のサイズです。
  * `ifftplan`: オーバーサンプリングされた逆FFTの計画。例えば、`ifftplan = plan_ifft(λ; flags=FFTW.MEASURE)` で計算します。ここで `shape` は再構成された画像のサイズです。
  * `xOS1`: `λ` のサイズの事前に割り当てられた配列。`xOS1 = similar(λ)` で事前に割り当てます。
  * `xOS2`: `λ` のサイズの事前に割り当てられた配列。`xOS2 = similar(λ)` で事前に割り当てます。

# 例

```jldoctest; output = false, setup = :(using NFFT, NFFTTools, Random; Random.seed!(1))
julia> using FFTW

julia> Nx = 32;

julia> trj = Float32.(rand(2, 1000) .- 0.5);

julia> λ = calculateToeplitzKernel((Nx, Nx), trj);

julia> xOS1 = similar(λ);

julia> xOS2 = similar(λ);

julia> fftplan = plan_fft(xOS1; flags=FFTW.MEASURE);

julia> ifftplan = plan_ifft(xOS1; flags=FFTW.MEASURE);

julia> y = randn(ComplexF32, Nx, Nx);

julia> convolveToeplitzKernel!(y, λ, fftplan, ifftplan, xOS1, xOS2)
32×32 Matrix{ComplexF32}:
  177.717-52.0493im   10.6059+20.7185im  …   746.131+330.005im
 -311.858+988.219im  -1216.83-1295.14im      410.732+751.925im
 -1082.27+872.968im   1023.97-1556.45im     -923.699+478.63im
 -999.035-525.161im  -1694.59-658.558im     -521.044+607.005im
 -342.999+1481.82im  -1729.18-2712.81im      56.5212+1394.81im
 -1187.65-1979.55im   1389.67+970.033im  …   2968.93-744.264im
 -666.533+485.511im  -1315.83+409.855im     -610.146+132.258im
  1159.57+64.6059im  -299.169-569.622im      663.802+396.827im
 -795.112-1464.63im   -462.43+2442.77im     -1622.72+1701.27im
 -1047.67+31.5578im  -1127.65-936.043im      474.071+797.911im
         ⋮                               ⋱
  327.345+2191.71im  -904.635+558.786im     -1449.32-276.721im
  -1047.2-71.362im    363.109+567.346im      -1974.0-2348.36im
 -1540.45+1661.77im   1175.75+1279.75im  …   1110.61+653.234im
 -526.832-435.297im  -265.021-2019.08im      68.5607-323.086im
 -1076.52-2719.16im  -477.005+2232.06im      -155.59-1275.66im
  1143.76-735.966im  -380.489+2485.78im      1812.17-261.191im
  1685.44-1243.29im   1911.16-1157.72im     -991.639-42.8214im
  1054.11-1282.41im   66.9358-588.991im  …  -952.238+1026.35im
 -417.276-273.367im  -946.698+1971.77im     -890.339-882.05im

```
