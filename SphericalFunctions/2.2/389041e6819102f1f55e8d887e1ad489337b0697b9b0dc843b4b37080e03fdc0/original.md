```
sYlm_iterator(Y, ℓₘₐₓ, [ℓₘᵢₙ, [iₘᵢₙ]])
```

Construct an Iterator that returns sub-vectors of `Y`, each of which consists of elements $(ℓ,-ℓ)$ through $(ℓ,ℓ)$, for $ℓ$ from `ℓₘᵢₙ` through `ℓₘₐₓ`.

Note that the returned objects are *views* into the original `Y` data — meaning that you may alter their values.

Because the result is a vector restricted to a particular $ℓ$ value, you can index the $(ℓ, m)$ element as `[ℓ+m+1]`.  For example, you might use this as something like

```
for (ℓ, Yˡ) in zip(ℓₘᵢₙ:ℓₘₐₓ, sYlm_iterator(Y, ℓₘₐₓ))
    for m in -ℓ:ℓ
        Yˡ[ℓ+m+1]  # ... do something with Yˡ
    end
end
```

By default, `Y` is assumed to contain all possible values, beginning with `(0,0)`.  However, if `ℓₘᵢₙ` is not 0, this can be ambiguous: do we mean that `Y` really starts with the `(0,0)` element and we are just asking to begin the iteration higher?  Or do we mean that `Y` doesn't even contain data for lower `ℓ` values?  We can resolve this using `iₘᵢₙ`, which gives the index of `ℓₘᵢₙ` in `Y`.  By default, we assume the first case, and set `iₘᵢₙ=Ysize(ℓₘᵢₙ-1)+1`. However, if `Y` doesn't contain data below `ℓₘᵢₙ`, we could use `iₘᵢₙ=1` to indicate the index in `Y` at which to find $(ℓₘᵢₙ,-ℓₘᵢₙ)$.

Also note that no bounds checking is done, either at instantiation time or during iteration.  You are responsible for ensuring that the size of `Y` and the values of `ℓₘₐₓ`, `ℓₘᵢₙ`, and `iₘᵢₙ` make sense.
