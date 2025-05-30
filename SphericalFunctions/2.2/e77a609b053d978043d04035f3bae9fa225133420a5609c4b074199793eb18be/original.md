```
Yindex(ℓ, m, ℓₘᵢₙ=0)
```

Compute index into array of mode weights

## Parameters

ℓ : int     Integer satisfying ℓₘᵢₙ <= ℓ <= ℓₘₐₓ m : int     Integer satisfying -ℓ <= m <= ℓ ℓₘᵢₙ : int, optional     Integer satisfying 0 <= ℓₘᵢₙ.  Defaults to 0.

## Returns

i : int     Index of a particular element of the mode-weight array as described below

## See Also

Ysize : Total size of array of mode weights Yrange : Array of (ℓ, m) indices corresponding to this array

## Notes

This assumes that the modes are arranged (with fixed s value) as

```
[
    Y(s, ℓ, m)
    for ℓ ∈ ℓₘᵢₙ:ℓₘₐₓ
    for m ∈ -ℓ:ℓ
]
```
