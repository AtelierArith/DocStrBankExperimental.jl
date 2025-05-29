```
dataspace(data)
```

The default `Dataspace` used for representing a Julia object `data`:

  * strings or numbers: a scalar `Dataspace`
  * arrays: a simple `Dataspace`
  * `struct` types: a scalar `Dataspace`
  * `nothing` or an `EmptyArray`: a null dataspace
