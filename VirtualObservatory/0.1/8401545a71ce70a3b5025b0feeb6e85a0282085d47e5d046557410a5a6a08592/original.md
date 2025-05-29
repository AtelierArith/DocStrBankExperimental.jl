```
VizierCatalog(id, [cols=All()]; [unitful=false])
```

A catalog from the [VizieR](https://vizier.u-strasbg.fr/) database, identified by its `id` (e.g. `"J/ApJS/260/4/table2"`).

Main capabilities:

  * Download as a raw file: `download(::VizierCatalog)`
  * Retrieve as a Julia table (`StructArray`): `table(::VizierCatalog)`
  * Crossmatch using the [CDS X-Match service](https://cdsxmatch.u-strasbg.fr/xmatch): the `FlexiJoins` interface, `innerjoin((; ::VizierCatalog, tbl), by_distance(identity, ..., separation, <=(...)))`

Arguments control accessing or processing the catalog:

  * `cols=All()`: only retrieve selected columns
  * `unitful=false`: whether to parse columns with units into `Unitful.jl` values
  * `table_format="votable"`: format of the downloaded table, only supported for downloading the raw file
