```
Represents the configuration of the data scraping process from OSM XML.
```

Only those pieces of data will be scraped that are defined here.

The configuration is defined in a DataFrame with the following columns: `group`, `key`, `values`, `influence`, `range`. Instead of the DataFrame a paths to a CSV file can be provided.

### Constructors

  * `ScrapePOIConfig()` - default inbuilt configuration for data scraping.  Note that the default configuration can change with library updates.  This will use a default configuration and `AttractivenessMetaPOI` as meta data.
  * `ScrapePOIConfig(keys::Union{Tuple{String,String}, String}...)` - provide keys for scraping, `NoneMetaPOI` will be used as metadata
  * `ScrapePOIConfig(pairs::Pair{<:Union{Tuple{String,String}, String}, T}...)` - provide keys and corresponding metadata
  * `ScrapePOIConfig{T <: AbstractMetaPOI}(df::DataFrame)` - use a `DataFrame` as configuration
  * ScrapePOIConfig{T <: AbstractMetaPOI}(meta::Dict{<:Union{String, Tuple{String,String}}, T}) - internal constructor. `meta` dictionary explaining how a single `k="keyname"` value or tuple ofvalues (paired with `v="valuename"`) should be mapped for attractiveness metadata.

### Example

```julia ScrapePOIConfig(("amenity", "parking"), ("parking"))

ScrapePOIConfig(("*", "restaurant"))

ScrapePOIConfig("*")

ScrapePOIConfig(("amenity", "parking") =>AttractivenessMetaPOI(:car, 1, 500), ("amenity", "restaurant") => (AttractivenessMetaPOI(:food, 1.0, 1000.0)))

ScrapePOIConfig([("amenity", "pub"), ("amenity", "restaurant")] .=> Ref(AttractivenessMetaPOI(:food, 1.0, 100.0)))
