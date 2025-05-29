```
dirichlet_beta()
```

ディリクレベータ関数を計算します、      [https://en.wikipedia.org/wiki/Dirichlet*beta*function](https://en.wikipedia.org/wiki/Dirichlet_beta_function)

## 引数

  * $$
    s
    $$

    `::Number`: どのタイプの数でも動作するはずですが、主に `Complex{Float64}` でテストされています。

## 例

```jldoctest; setup = :(using Polylogarithms)
julia> dirichlet_beta(1.5)
0.8645026534612017
```
