```
metaphlan_profiles(path::AbstractString, rank::Union{Int, Symbol}=:all; keepunidentified=false)
```

Reads in MetaPhlAn profiles from a merged table into a CommunityProfile. Can select data according to taxonomic rank. If rank not given, all data is used. Set `keepunidentified` flag to `true` to keep `UNIDENTIFIED` data.

Levels may be given either as numbers or symbols:

  * `1` = `:kingdom`
  * `2` = `:phylum`
  * `3` = `:class`
  * `4` = `:order`
  * `5` = `:family`
  * `6` = `:genus`
  * `7` = `:species`
  * `8` = `:subspecies`
