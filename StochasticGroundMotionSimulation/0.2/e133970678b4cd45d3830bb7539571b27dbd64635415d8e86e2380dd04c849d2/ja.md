```
transfer(f::Vector{T}, sdof::Oscillator) where T<:Real
```

単一自由度振動子の周波数ベクトルに対する伝達関数のモジュラスを計算します。

  * `f::Vector` は周波数のベクトルです
  * `sdof::Oscillator` は振動子のインスタンスです

# 例

```julia-repl
  f = collect(range(0.1, stop=10.0, step=0.01))
  sdof = Oscillator(1.0)
  Hf = transfer(f, sdof)
```
