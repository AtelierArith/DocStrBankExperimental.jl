If 

  * μ is an `AbstractMeasure` or satisfies the Measure interface, and
  * k is a function taking values from the support of μ and returning a measure

Then `μ ↣ k` is a measure, called a *monadic bind*. In a probabilistic programming language like Soss.jl, this could be expressed as

Note that bind is usually written `>>=`, but this symbol is unavailable in Julia.

```
bind = @model μ,k begin 
    x ~ μ
    y ~ k(x)
    return y
end
```

See also `bind` and `Bind`
