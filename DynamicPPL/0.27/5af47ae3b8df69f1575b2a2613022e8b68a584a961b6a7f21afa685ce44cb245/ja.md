```
pointwise_loglikelihoods(model::Model, chain::Chains, keytype = String)
```

`model`を`chain`内の各サンプルに対して実行し、観測のシンボルに対応するキーと、形状が`(num_chains, num_samples)`の行列を値とする`OrderedDict{String, Matrix{Float64}}`を返します。

`keytype`は、返される`OrderedDict`で使用されるキーの型を指定します。現在、サポートされているのは`String`と`VarName`のみです。

# 注意事項

`y`が`n`個のi.i.d. `Normal(μ, σ)`変数の`Vector`で、`μ`と`σ`の両方が`<:Real`であるとします。このとき、*observe*（すなわち左辺が*観測*であるとき）文は3つの方法で実装できます。

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

```julia-repl
julia> using DynamicPPL, Turing

julia> @model function demo(xs, y)
           s ~ InverseGamma(2, 3)
           m ~ Normal(0, √s)
           for i in eachindex(xs)
               xs[i] ~ Normal(m, √s)
           end

           y ~ Normal(m, √s)
       end
demo (generic function with 1 method)

julia> model = demo(randn(3), randn());

julia> chain = sample(model, MH(), 10);

julia> pointwise_loglikelihoods(model, chain)
OrderedDict{String,Array{Float64,2}} with 4 entries:
  "xs[1]" => [-1.42932; -2.68123; … ; -1.66333; -1.66333]
  "xs[2]" => [-1.6724; -0.861339; … ; -1.62359; -1.62359]
  "xs[3]" => [-1.42862; -2.67573; … ; -1.66251; -1.66251]
  "y"     => [-1.51265; -0.914129; … ; -1.5499; -1.5499]

julia> pointwise_loglikelihoods(model, chain, String)
OrderedDict{String,Array{Float64,2}} with 4 entries:
  "xs[1]" => [-1.42932; -2.68123; … ; -1.66333; -1.66333]
  "xs[2]" => [-1.6724; -0.861339; … ; -1.62359; -1.62359]
  "xs[3]" => [-1.42862; -2.67573; … ; -1.66251; -1.66251]
  "y"     => [-1.51265; -0.914129; … ; -1.5499; -1.5499]

julia> pointwise_loglikelihoods(model, chain, VarName)
OrderedDict{VarName,Array{Float64,2}} with 4 entries:
  xs[1] => [-1.42932; -2.68123; … ; -1.66333; -1.66333]
  xs[2] => [-1.6724; -0.861339; … ; -1.62359; -1.62359]
  xs[3] => [-1.42862; -2.67573; … ; -1.66251; -1.66251]
  y     => [-1.51265; -0.914129; … ; -1.5499; -1.5499]
```

## ブロードキャスティング

`x .~ Dist()`は、`x`を単一の観測ではなく*独立した*観測のコレクションとして扱うことに注意してください。

```jldoctest; setup = :(using Distributions)
julia> @model function demo(x)
           x .~ Normal()
       end;

julia> m = demo([1.0, ]);

julia> ℓ = pointwise_loglikelihoods(m, VarInfo(m)); first(ℓ[@varname(x[1])])
-1.4189385332046727

julia> m = demo([1.0; 1.0]);

julia> ℓ = pointwise_loglikelihoods(m, VarInfo(m)); first.((ℓ[@varname(x[1])], ℓ[@varname(x[2])]))
(-1.4189385332046727, -1.4189385332046727)
```
