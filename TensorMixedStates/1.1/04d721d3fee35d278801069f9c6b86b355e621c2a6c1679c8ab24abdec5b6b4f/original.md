```
@def_states(site, symbols)
```

define the given states for the given site

# Example

```
@def_states(Fermion(),
[
    ["Emp", "0"] => [1., 0.],
    "Occ" => [0., 1.],
])
```
