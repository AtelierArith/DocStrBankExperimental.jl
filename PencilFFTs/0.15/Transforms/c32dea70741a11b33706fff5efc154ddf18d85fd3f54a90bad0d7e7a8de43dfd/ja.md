異なる一次元FFTベースの変換を定義します。

これらの変換はすべて[`AbstractTransform`](@ref)型のサブタイプです。

可能な場合、変換の名前は[`AbstractFFTs.jl`](https://juliamath.github.io/AbstractFFTs.jl/stable/api/)および[`FFTW.jl`](https://juliamath.github.io/FFTW.jl/stable/fft/)によってエクスポートされた関数と一貫性を保っています。
