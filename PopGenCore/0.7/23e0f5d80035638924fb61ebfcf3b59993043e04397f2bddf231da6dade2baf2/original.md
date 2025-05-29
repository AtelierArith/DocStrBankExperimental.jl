```
locationdata!(data::PopData; longitude::Vector{Float64}, latitude::Vector{Float64})
```

Replaces existing `PopData` geographic coordinate data. Takes **decimal degrees** as a `Vector` of any `AbstractFloat`.

## Formatting requirements

  * Decimal Degrees format: `-11.431`
  * **Must** use negative sign `-` instead of cardinal directions
  * Location data must be in the order that samples appear in your `PopData`
  * Missing data should be coded as `missing` values of type `Missing` (can be accomplished with `replace!()`)

### Example

```
ncats = @nancycats ;
x = rand(237) ; y = rand(237)
locationdata!(ncats, longitude = x, latitude = y)
```
