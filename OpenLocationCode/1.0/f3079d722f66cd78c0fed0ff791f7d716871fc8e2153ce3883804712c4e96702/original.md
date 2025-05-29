```
encode(latitude, longitude[, codelength])
```

Encode a location into an Open Location Code. Produces a code of the specified length, or the default length if no length is provided.

The length determines the accuracy of the code. The default length is 10 characters, returning a code of approximately 13.9x13.9 meters. Longer codes represent smaller areas, but lengths > 15 are sub-centimetre and so 11 or 12 are probably the limit of useful codes.

# Arguments

  * `latitude`: A latitude in signed degrees. Will be clipped to the range -90 to 90.
  * `longitude`: A longitude in signed degrees. Will be normalised to   the range -180 to 180.
  * `codelength`: The number of significant digits in the output code, not   including any separator characters.

# Examples:

```julia
julia> encode(50.173168, 8.338086, 11)
"9F2C58FQ+768"
```
