```
harmonic(n::Integer,r::Integer)
```

一般化調和数を計算します。例えば、[http://mathworld.wolfram.com/HarmonicNumber.html](http://mathworld.wolfram.com/HarmonicNumber.html)を参照してください。両方の入力が整数のときに機能するより良いアプローチを使用しています。[https://carma.newcastle.edu.au/resources/jon/Preprints/Papers/Published-InPress/Oscillatory%20(Tapas%20II)/Papers/coffey-zeta.pdf](https://carma.newcastle.edu.au/resources/jon/Preprints/Papers/Published-InPress/Oscillatory%20(Tapas%20II)/Papers/coffey-zeta.pdf)、p.341

## 引数

  * $$
    n
    $$

    `::Integer`: 計算する調和数の非負インデックス1
  * $$
    r
    $$

    `::Integer`: 計算する調和数のインデックス2

## 例

```jldoctest; setup = :(using Polylogarithms)
julia> harmonic(2,1)
1.5000000000000002
```
