```
metaphlan_profile(path::AbstractString, rank::Union{Int, Symbol}=:all; sample::AbstractString=basename(first(splitext(path))))
```

Creates a CommunityProfile from a MetaPhlAn output file. Can select data according to taxonomic rank. If rank not given, all data is used. `Sample name` of the CommunityProfile can be specified by passing a `sample` argument. If name not given, the name of the file becomes the `Sample name`.

Levels may be given either as numbers or symbols:

  * `1` = `:kingdom`
  * `2` = `:phylum`
  * `3` = `:class`
  * `4` = `:order`
  * `5` = `:family`
  * `6` = `:genus`
  * `7` = `:species`
  * `8` = `:subspecies`
