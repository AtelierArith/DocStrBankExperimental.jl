```
@addlogprob!(ex)
```

Add the result of the evaluation of `ex` to the joint log probability.

# Examples

This macro allows you to [include arbitrary terms in the likelihood](https://github.com/TuringLang/Turing.jl/issues/1332)

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

and to [reject samples](https://github.com/TuringLang/Turing.jl/issues/1328):

```jldoctest; setup = :(using Distributions, LinearAlgebra)
julia> @model function demo(x)
           m ~ MvNormal(zero(x), I)
           if dot(m, x) < 0
               @addlogprob! -Inf
               # Exit the model evaluation early
               return
           end
           x ~ MvNormal(m, I)
           return
       end;

julia> logjoint(demo([-2.1]), (m=[0.2],)) == -Inf
true
```

!!! note
    The `@addlogprob!` macro increases the accumulated log probability regardless of the evaluation context, i.e., regardless of whether you evaluate the log prior, the log likelihood or the log joint density. If you would like to avoid this behaviour you should check the evaluation context. It can be accessed with the internal variable `__context__`. For instance, in the following example the log density is not accumulated when only the log prior is computed:

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

