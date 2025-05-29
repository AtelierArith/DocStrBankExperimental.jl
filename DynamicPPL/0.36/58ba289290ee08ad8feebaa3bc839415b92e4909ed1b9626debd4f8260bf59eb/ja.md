```
pointwise_logdensities(model::Model, chain::Chains, keytype = String)
```

`chain`内の各サンプルに対して`model`を実行し、変数のシンボルに対応するキーと、形状が`(num_chains, num_samples)`の行列を値とする`OrderedDict{String, Matrix{Float64}}`を返します。

`keytype`は返される`OrderedDict`で使用されるキーの型を指定します。現在、サポートされているのは`String`と`VarName`のみです。

# 注意事項

`y`が`n`個のi.i.d. `Normal(μ, σ)`変数の`Vector`で、`μ`と`σ`の両方が`<:Real`であるとします。この場合、*observe*（すなわち左辺が*観測*であるとき）文は3つの方法で実装できます。

1. `for`ループを使用する方法：

```julia
for i in eachindex(y)
    y[i] ~ Normal(μ, σ)
end
```

2. `.~`を使用する方法：

```julia
y .~ Normal(μ, σ)
```

3. `MvNormal`を使用する方法：

```julia
y ~ MvNormal(fill(μ, n), σ^2 * I)
```

(1)および(2)では、`y`は`n`個のi.i.d. 1次元変数のコレクションとして扱われますが、(3)では`y`は*単一*のn次元観測として扱われます。

これは特に、計算が下流の計算に使用される場合に重要です。

# 例

## チェーンから

```jldoctest pointwise-logdensities-chains; setup=:(using Distributions)
julia> using MCMCChains

julia> @model function demo(xs, y)
           s ~ InverseGamma(2, 3)
           m ~ Normal(0, √s)
           for i in eachindex(xs)
               xs[i] ~ Normal(m, √s)
           end
           y ~ Normal(m, √s)
       end
demo (generic function with 2 methods)

julia> # 例の観測。
       model = demo([1.0, 2.0, 3.0], [4.0]);

julia> # 3回の反復を持つチェーン。
       chain = Chains(
           reshape(1.:6., 3, 2),
           [:s, :m]
       );

julia> pointwise_logdensities(model, chain)
OrderedDict{String, Matrix{Float64}} with 6 entries:
  "s"     => [-0.802775; -1.38222; -2.09861;;]
  "m"     => [-8.91894; -7.51551; -7.46824;;]
  "xs[1]" => [-5.41894; -5.26551; -5.63491;;]
  "xs[2]" => [-2.91894; -3.51551; -4.13491;;]
  "xs[3]" => [-1.41894; -2.26551; -2.96824;;]
  "y"     => [-0.918939; -1.51551; -2.13491;;]

julia> pointwise_logdensities(model, chain, String)
OrderedDict{String, Matrix{Float64}} with 6 entries:
  "s"     => [-0.802775; -1.38222; -2.09861;;]
  "m"     => [-8.91894; -7.51551; -7.46824;;]
  "xs[1]" => [-5.41894; -5.26551; -5.63491;;]
  "xs[2]" => [-2.91894; -3.51551; -4.13491;;]
  "xs[3]" => [-1.41894; -2.26551; -2.96824;;]
  "y"     => [-0.918939; -1.51551; -2.13491;;]

julia> pointwise_logdensities(model, chain, VarName)
OrderedDict{VarName, Matrix{Float64}} with 6 entries:
  s     => [-0.802775; -1.38222; -2.09861;;]
  m     => [-8.91894; -7.51551; -7.46824;;]
  xs[1] => [-5.41894; -5.26551; -5.63491;;]
  xs[2] => [-2.91894; -3.51551; -4.13491;;]
  xs[3] => [-1.41894; -2.26551; -2.96824;;]
  y     => [-0.918939; -1.51551; -2.13491;;]
```

## ブロードキャスティング

`x .~ Dist()`は、`x`を単一の観測ではなく*独立した*観測のコレクションとして扱うことに注意してください。

```jldoctest; setup = :(using Distributions)
julia> @model function demo(x)
           x .~ Normal()
       end;

julia> m = demo([1.0, ]);

julia> ℓ = pointwise_logdensities(m, VarInfo(m)); first(ℓ[@varname(x[1])])
-1.4189385332046727

julia> m = demo([1.0; 1.0]);

julia> ℓ = pointwise_logdensities(m, VarInfo(m)); first.((ℓ[@varname(x[1])], ℓ[@varname(x[2])]))
(-1.4189385332046727, -1.4189385332046727)
```
