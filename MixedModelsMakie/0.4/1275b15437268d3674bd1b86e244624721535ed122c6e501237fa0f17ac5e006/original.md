```
qqcaterpillar(m::MixedModel, gf::Symbol=first(fnames(m));
              kwargs...)
```

Returns a `Figure` of a "qq-caterpillar plot" of the random-effects means and prediction intervals.

`gf` specifies which grouping variable is displayed.

`kwargs...` are passed on to [`qqcaterpillar!`](@ref).
