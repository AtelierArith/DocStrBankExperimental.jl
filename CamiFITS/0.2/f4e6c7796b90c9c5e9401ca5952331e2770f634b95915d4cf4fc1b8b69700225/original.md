```
cast_FITS_card(cardindex::Int, record::String)
```

Create the [`FITS_card`](@ref) object for `record` with index `cardindex`.

#### Example:

```
julia> record = "SIMPLE  =                    T / file does conform to FITS standard             ";

julia> card = cast_FITS_card(1, record);

julia> card.cardindex, card.keyword, card.value, card.comment
(1, "SIMPLE", true, "file does conform to FITS standard             ")
```
