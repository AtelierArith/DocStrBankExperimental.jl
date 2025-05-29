**Representation of a GBIF taxon**

All taxonomic level fields can either be `missing`, or a pair linking the name of the taxon/level to its unique key in the GBIF database.

`name` - the vernacular name of the taxon

`scientific` - the accepted scientific name of the species

`status` - the status of the taxon

`match` - the type of match

`kingdom` - a `Pair` linking the name of the kingdom to its unique ID

`phylum` - a `Pair` linking the name of the phylum to its unique ID

`class` - a `Pair` linking the name of the class to its unique ID

`order` - a `Pair` linking the name of the order to its unique ID

`family` - a `Pair` linking the name of the family to its unique ID

`genus` - a `Pair` linking the name of the genus to its unique ID

`species` - a `Pair` linking the name of the species to its unique ID

`confidence` - an `Int64` to note the confidence in the match

`synonym` - a `Boolean` indicating whether the taxon is a synonym
