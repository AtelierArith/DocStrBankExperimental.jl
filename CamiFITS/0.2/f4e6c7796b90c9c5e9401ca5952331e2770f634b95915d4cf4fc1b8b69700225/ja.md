```
cast_FITS_card(cardindex::Int, record::String)
```

`cardindex`のインデックスを持つ`record`の[`FITS_card`](@ref)オブジェクトを作成します。

#### 例:

```
julia> record = "SIMPLE  =                    T / file does conform to FITS standard             ";

julia> card = cast_FITS_card(1, record);

julia> card.cardindex, card.keyword, card.value, card.comment
(1, "SIMPLE", true, "file does conform to FITS standard             ")
```
