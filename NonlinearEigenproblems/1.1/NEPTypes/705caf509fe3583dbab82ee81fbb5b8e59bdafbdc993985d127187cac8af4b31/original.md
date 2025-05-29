```
struct DefaultErrmeasure <: Errmeasure
function DefaultErrmeasure(nep::NEP)
```

When you specify this `Errmeasure`, NEP-PACK tries to determine a suitable `Errmeasure` based on the type of the `NEP`. Note that this behavior may change in future versions.

See also: [`Errmeasure`](@ref)
