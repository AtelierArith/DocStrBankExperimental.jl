```
Sample(size, [weights]; replace=true, ordered=false, rng=default_rng())
```

`weights`に応じて、オプション`replace`に従って、テーブルの`size`行をサンプリングします。オプション`ordered`を使用すると、元のテーブルと同じ順序でサンプルを返すことができます。

# 例

```julia
Sample(1000)
Sample(1000, replace=false)
Sample(1000, replace=false, ordered=true)

# rngを使用して
using Random
rng = MersenneTwister(2)
Sample(1000, rng=rng)

# weightsを使用して
Sample(10, rand(100))
```
