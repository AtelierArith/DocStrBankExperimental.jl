```markdown
convertmarg!(X::Matrix, d::UnionAll, p::Vector{Vector})

サイズが(size(X,2) = n)のランダム変数の実現の行列Xを取り、iで番号付けされた一様周辺を共通分布dに変換し、パラメータp[i]を使用します。`testunif = true`の場合、各周辺が一様性のテストを受けます。

```

jldoctest julia> Random.seed!(43);

julia> x = rand(10,2);

julia> convertmarg!(x, Normal, [[0, 1],[0, 10]])

julia> x 10×2 Array{Float64,2}:  -0.911655    4.17328   0.756673  -14.4472   1.22088   -11.4823   1.43866   -13.1053  -0.231978  -11.2415   1.35696     6.43914   0.949145  -26.0172  -0.251957  -18.9723  -0.177808Real4172   1.70477    10.4192

```

```
