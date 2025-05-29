```
bernoulli(n)
```

最初の35個のベルヌーイ数 $B_n$ （第一種またはNISTタイプ）を計算します。例えば、次を参照してください。

  * [http://mathworld.wolfram.com/BernoulliNumber.html](http://mathworld.wolfram.com/BernoulliNumber.html)
  * [https://en.wikipedia.org/wiki/Bernoulli_number](https://en.wikipedia.org/wiki/Bernoulli_number)
  * [http://dlmf.nist.gov/24](http://dlmf.nist.gov/24)

注：第二種のベルヌーイ数は、$B_1 = + 1/2$（-1/2の代わり）であることを除いて異なるようです。

## 引数

  * $$
    n
    $$

    `::Integer`: シリーズのインデックス、$n=0,1,2,3,...,35$ （より大きな $n$ の場合は `bernoulli(n,0.0)` を使用してください）

最初の36個の値のみを提供します。これを超えると、Int64の有理数を返すことができないため、`bernoulli(n,0.0)` を使用して実数近似を計算するのが最良です。

$$
n>1
$$

の奇数値はすべてゼロです。

## 例

```jldoctest; setup = :(using Polylogarithms)
julia> bernoulli(6)
1//42
```
