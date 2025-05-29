```
logpdf_with_trans(d::Distribution, x, transform::Bool)
```

`transform`が`false`の場合、`logpdf_with_trans`は分布`d`の`x`における対数確率密度関数（logpdf）を計算します。

`transform`が`true`の場合、`x`は分布`d`の制約付きから非制約付きの双射を使用して変換され、その後、結果の値に対する非制約（変換された）分布に関してlogpdfが計算されます。言い換えれば、`x`が`d`に従って分布し、`y = link(d, x)`が`td = transformed(d)`に従って分布している場合、`logpdf_with_trans(d, x, true) = logpdf(td, y)`となります。これは変換の対数ヤコビアンを引くことによって達成されます。

# 例

```jldoctest
julia> using Bijectors

julia> logpdf_with_trans(LogNormal(), ℯ, false)
-2.4189385332046727

julia> logpdf(LogNormal(), ℯ)  # 上と同じ
-2.4189385332046727

julia> logpdf_with_trans(LogNormal(), ℯ, true)
-1.4189385332046727

julia> # もし x ~ LogNormal() ならば log(x) ~ Normal()
       logpdf(Normal(), 1.0)   
-1.4189385332046727

julia> # 両者の違いはヤコビアンによるもの
       logabsdetjac(bijector(LogNormal()), ℯ)
-1
```
