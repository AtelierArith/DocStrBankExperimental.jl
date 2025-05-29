```
 generate_mnmm_data(N::Int64, D::Int64, K::Int64, trials::Int64)
```

`K`の`D`特徴の多項分布ベクトルから生成された`N`の観測値を生成し、各ベクトルから`trials`のサンプルを引きます。

`(Samples, Labels, Vectors)`を返します。

# 例

```julia
julia> generate_mnmm_data(10000, 10, 5, 100)
...
```
