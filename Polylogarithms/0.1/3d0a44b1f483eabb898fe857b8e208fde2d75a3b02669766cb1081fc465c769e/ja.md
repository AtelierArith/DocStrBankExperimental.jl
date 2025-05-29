```
harmonic(n::Integer,r::Real)
```

一般化調和数を計算します。例として、[http://mathworld.wolfram.com/HarmonicNumber.html](http://mathworld.wolfram.com/HarmonicNumber.html)を参照してください。

## 引数

  * $$
    n
    $$

    `::Integer`: 計算する調和数の非負インデックス1
  * $$
    r
    $$

    `::Real`: 計算する調和数のインデックス2

複素数のrに拡張することも可能ですが、それにはさらなるテストが必要です。

## 例

```jldoctest; setup = :(using Polylogarithms)
julia> harmonic(2,1.5)
1.3535533905932737
```
