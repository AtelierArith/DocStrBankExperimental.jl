```
GumbelCopulaRev
```

フィールド:

  * n::Int - マージナルの数
  * θ::Real - パラメータ

コンストラクタ

```
GumbelCopulaRev(n::Int, θ::Real)
```

逆Gumbelコピュラ（逆とはu → 1 .- uを意味します）、θ::Real ∈ [1, ∞)でパラメータ化され、n::Int ≧ 2に対応しています。

コンストラクタ

```
GumbelCopulaRev(n::Int, θ::Real, cor::Type{<:CorrelationType})
```

期待相関からコピュラパラメータを計算するために、空の型cor::Type{<:CorrelationType}を使用します。ここで、SpearmanCorrelation <:CorrelationTypeおよびKendallCorrelation<:CorrelationTypeです。corを使用する場合は、コンストラクタ内のθの位置に期待相関を置きます。コピュラパラメータはその後計算されます。相関はゼロより大きくなければなりません。

```jldoctest
julia> c = GumbelCopulaRev(4, .75, KendallCorrelation)
GumbelCopulaRev(4, 4.0)

julia> Random.seed!(43);

julia> simulate_copula(2, c)
2×4 Array{Float64,2}:
 0.963524   0.872108  0.816626  0.783637
 0.0954475  0.138451  0.13593   0.0678172
```
