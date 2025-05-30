```
Ysize(ℓₘₐₓ)
```

Compute total size of array of mode weights

## See Also

Yrange : Array of (ℓ, m) indices corresponding to this array Yindex : Index of a particular element of the mode weight array

## Notes

This assumes that the modes are arranged (with fixed s value) as

```
[
    Y(s, ℓ, m)
    for ℓ ∈ ℓₘᵢₙ:ℓₘₐₓ
    for m ∈ -ℓ:ℓ
]
```
