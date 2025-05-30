```
Yrange(ℓₘᵢₙ, ℓₘₐₓ)
```

Create an array of (ℓ, m) indices as in Y array

## Parameters

ℓₘᵢₙ : int     Integer satisfying 0 <= ℓₘᵢₙ <= ℓₘₐₓ ℓₘₐₓ : int     Integer satisfying 0 <= ℓₘᵢₙ <= ℓₘₐₓ

## Returns

i : int     Total size of array of mode weights arranged as described below

## See Also

Ysize : Total size of array of mode weights Yindex : Index of a particular element of the mode weight array

## Notes

This assumes that the modes are arranged (with fixed s value) as

```
[
    Y(s, ℓ, m)
    for ℓ ∈ ℓₘᵢₙ:ℓₘₐₓ
    for m ∈ -ℓ:ℓ
]
```
