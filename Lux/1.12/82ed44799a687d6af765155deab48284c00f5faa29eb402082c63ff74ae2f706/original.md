```
NoOpLayer()
```

As the name suggests does nothing but allows pretty printing of layers. Whatever input is passed is returned.

# Example

```jldoctest
julia> model = NoOpLayer()
NoOpLayer()

julia> rng = Random.default_rng();
       Random.seed!(rng, 0);
       ps, st = Lux.setup(rng, model);
       x = 1
1

julia> y, st_new = model(x, ps, st)
(1, NamedTuple())
```
