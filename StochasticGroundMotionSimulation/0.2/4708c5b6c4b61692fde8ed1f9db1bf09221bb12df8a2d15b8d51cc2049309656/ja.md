```
transfer!(Hf::Vector{T}, f::Vector{T}, sdof::Oscillator) where T<:Real
```

単一自由度系（SDOF）の伝達関数のモジュラスを、周波数のベクトルに対してインプレースで計算します。	- `Hf::Vector` は結果が格納される事前に割り当てられたベクトルです。	- `f::Vector` は周波数のベクトルです。	- `sdof::Oscillator` はオシレーターのインスタンスです。

# 例

```julia-repl
    f = collect(range(0.1, stop=10.0, step=0.01))
    sdof = Oscillator(1.0)
    Hf = similar(f)
    transfer!(Hf, f, sdof)
```
