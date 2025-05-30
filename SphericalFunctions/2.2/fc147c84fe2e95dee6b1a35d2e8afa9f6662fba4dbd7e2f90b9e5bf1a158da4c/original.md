```
d_iterator(d, ℓₘₐₓ, [ℓₘᵢₙ])
```

Construct an Iterator that returns sub-matrices of `d`, each of which consists of elements $(ℓ,-ℓ,-ℓ)$ through $(ℓ,ℓ,ℓ)$, for $ℓ$ from `ℓₘᵢₙ` through `ℓₘₐₓ`.  By default, `ℓₘᵢₙ` is 0.

!!! danger "Inconsistent behavior"
    This iterator mistakenly returns the transpose of the result implied by this documentation.  As a result, a warning is issued every time this function is called. Rather than actually *fixing* this bug in this minor/patch version — which would be a breaking change — this is a final release in this major version of the package to notify users of this function (and `D_iterator`) that there is a problem.  The next major version of the package will likely change the actual behavior to the one implied by this docstring.  To quiet these warnings, you can temporarily pass the keyword argument `warn=false`, though this will probably be removed in the next major version. Alternatively, use `Dit = with_logger(NullLogger()) do D_iterator(...) end` to catch any warnings.


Note that the returned objects are *views* into the original `d` data — meaning that you may alter their values.

Because the result is a matrix restricted to a particular $ℓ$ value, you can index the $(ℓ, m′, m)$ element as `[ℓ+m′+1, ℓ+m+1]`.  For example, you might use this as something like

```
for (ℓ, dˡ) in zip(ℓₘᵢₙ:ℓₘₐₓ, d_iterator(d, ℓₘₐₓ))
    for m′ in -ℓ:ℓ
        for m in -ℓ:ℓ
            dˡ[ℓ+m′+1, ℓ+m+1]  # ... do something with dˡ
        end
    end
end
```

Also note that no bounds checking is done, either at instantiation time or during iteration. You are responsible for ensuring that the size of `d` and the values of `ℓₘₐₓ` and `ℓₘᵢₙ` make sense.
