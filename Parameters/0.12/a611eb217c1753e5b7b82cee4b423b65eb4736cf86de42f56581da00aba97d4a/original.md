As `@with_kw` but does not define a `show` method to avoid annoying redefinition warnings.

```julia
@with_kw_noshow struct MM{R}
    r::R = 1000.
    a::Int = 4
end
```

For more details see manual.
