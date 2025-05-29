```
Halo{X} <: Padding
```

Padding that uses an in-memory halo around the array so that parts of a stencil that go off the edge of the array can index directly into it without a bounds check or any conditional. This has the benefit of possibly better performance during window broadcasts, but some downsides.

In `:out` mode, a whole new array is alocated, larger than the original. This may not be worth doing unless you are using it multiple times. with `:in` mode, the outside edge of the array is used as padding. This may be more accurate  as there are no boundary effects from using a padding value.:w

# Example

```julia
halo_in = Halo(:in)
halo_out = Halo(:out)
```
