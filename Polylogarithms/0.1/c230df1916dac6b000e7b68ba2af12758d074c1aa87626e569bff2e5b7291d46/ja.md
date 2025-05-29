```
bernoulli(n, x)
```

ベルヌーイ多項式 $B_n(x)$ を計算します。例えば、次を参照してください。

  * [https://en.wikipedia.org/wiki/Bernoulli_polynomials](https://en.wikipedia.org/wiki/Bernoulli_polynomials)
  * [http://dlmf.nist.gov/24](http://dlmf.nist.gov/24)

## 引数

  * $$
    n
    $$

    `::Integer`: 数列のインデックス、$n=0,1,2,3,...$
  * $$
    x
    $$

    `::Real`: 多項式を計算する点

## 例

```jldoctest; setup = :(using Polylogarithms)
julia> bernoulli(6, 1.2)
0.008833523809524735
```
