```
occurrence_inventory(type::Symbol; kw...)
```

Return the number of occurrences for a taxon based on  certain criteria. The return value is a JSON3.jl object.

# Example

```
julia> country_counts = occurrence_inventory(:countries)
JSON3.Object{Vector{UInt8}, Vector{UInt64}} with 252 entries:
  :UNITED_STATES  => 816855696
  :CANADA         => 133550183
  :FRANCE         => 119683053
  :SWEDEN         => 116451484
  :AUSTRALIA      => 115239040
  :UNITED_KINGDOM => 108417142
  :NETHERLANDS    => 85750415
  :SPAIN          => 54804973
  :DENMARK        => 49334935
  :GERMANY        => 49290658
  :NORWAY         => 48337823
  :FINLAND        => 36970838
  :BELGIUM        => 35064346
  :SOUTH_AFRICA   => 33185318
  :INDIA          => 32071907
  :MEXICO         => 26295593
  :BRAZIL         => 24558941
  :COSTA_RICA     => 21103286
  :COLOMBIA       => 20143253
  :SWITZERLAND    => 17727317
  :PORTUGAL       => 17688228
  ⋮               => ⋮

julia> country_counts.INDIA
32071907
```

# Keywords

  * `type`: inventory accross categories, with additional keywords from:

`(basisOfRecord = (), countries = :publishingCountry, datasets = (:country, :taxonKey), publishingCountry = (:publishingCountry,), year = (:year,))`

Occurrence counts have a complicated schema of allowed keyword combinations. You can access these from the GBIF api using `occurrence_count_schema()`.
