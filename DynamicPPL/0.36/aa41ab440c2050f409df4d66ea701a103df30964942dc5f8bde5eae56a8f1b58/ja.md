```
@addlogprob!(ex)
```

`ex`の評価結果を結合対数確率に追加します。

# 例

このマクロを使用すると、[尤度に任意の項を含める](https://github.com/TuringLang/Turing.jl/issues/1332)ことができます。

```jldoctest; setup = :(using Distributions)
julia> myloglikelihood(x, μ) = loglikelihood(Normal(μ, 1), x);

julia> @model function demo(x)
           μ ~ Normal()
           @addlogprob! myloglikelihood(x, μ)
       end;

julia> x = [1.3, -2.1];

julia> loglikelihood(demo(x), (μ=0.2,)) ≈ myloglikelihood(x, 0.2)
true
```

また、[サンプルを拒否する](https://github.com/TuringLang/Turing.jl/issues/1328)ためにも使用できます：

```jldoctest; setup = :(using Distributions, LinearAlgebra)
julia> @model function demo(x)
           m ~ MvNormal(zero(x), I)
           if dot(m, x) < 0
               @addlogprob! -Inf
               # モデル評価を早期に終了
               return
           end
           x ~ MvNormal(m, I)
           return
       end;

julia> logjoint(demo([-2.1]), (m=[0.2],)) == -Inf
true
```

!!! note
    `@addlogprob!`マクロは、評価コンテキストに関係なく、累積対数確率を増加させます。つまり、対数事前、対数尤度、または対数結合密度を評価しているかどうかに関係なく増加します。この動作を避けたい場合は、評価コンテキストを確認する必要があります。これは内部変数`__context__`を使用してアクセスできます。たとえば、以下の例では、対数事前のみが計算されるときに対数密度は累積されません：

    ```jldoctest; setup = :(using Distributions)
    julia> myloglikelihood(x, μ) = loglikelihood(Normal(μ, 1), x);

    julia> @model function demo(x)
               μ ~ Normal()
               if DynamicPPL.leafcontext(__context__) !== PriorContext()
                   @addlogprob! myloglikelihood(x, μ)
               end
           end;

    julia> x = [1.3, -2.1];

    julia> logprior(demo(x), (μ=0.2,)) ≈ logpdf(Normal(), 0.2)
    true

    julia> loglikelihood(demo(x), (μ=0.2,)) ≈ myloglikelihood(x, 0.2)
    true
    ```

