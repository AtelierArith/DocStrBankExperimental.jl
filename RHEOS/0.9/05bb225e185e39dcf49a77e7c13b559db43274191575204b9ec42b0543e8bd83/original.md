```
getparams(m::RheoModel; unicode=true)
```

`getparams` return the list of model parameters with their values as a NamedTuple. If `unicode` is set to `false`, the unicode symbols are converted their text equivalent.

# Example

```@example
julia> model = RheoModel(Maxwell, k=1, η=2.)
[...]

julia> getparams(m)
(k = 1.0, η = 2.0)

julia> getparams(m,unicode=false)
(k = 1.0, eta = 2.0)
```
