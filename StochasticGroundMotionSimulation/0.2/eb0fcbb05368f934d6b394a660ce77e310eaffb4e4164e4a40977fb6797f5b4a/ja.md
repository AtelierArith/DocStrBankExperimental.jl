```
squared_transfer!(Hf2::Vector{T}, f::Vector{T}, sdof::Oscillator) where T<:Real
```

単一自由度振動子の伝達関数のモジュラスの二乗を、周波数のベクトルに対してインプレースで計算します：	- `Hf2::Vector` は結果が格納される事前に割り当てられたベクトルです     - `f::Vector` は周波数のベクトルです     - `sdof::Oscillator` は振動子のインスタンスです 入力は `Real` 型から派生しており、微分可能です。

# 例

```julia-repl
    f = collect(range(0.1, stop=10.0, step=0.01))
    sdof = Oscillator(1.0)
    Hf2 = similar(f)
    squared_transfer!(Hf2, f, sdof)
```
