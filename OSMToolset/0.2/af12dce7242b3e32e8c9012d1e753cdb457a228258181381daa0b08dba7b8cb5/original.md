```
find_poi(filename::AbstractString, scrape_config::ScrapePOIConfig{T <: AbstractMetaPOI}=ScrapePOIConfig(); all_tags::Bool=false)
```

Generates a `DataFrame` with points of interests and from a given XML `filename`. The `scrape_config` parameter defines the configuration of the scraping process. The data frame will also contain the metadata of type `T` for each POI.

The `DataFrame` can be later used with `AttractivenessSpatIndex` to build an attractivenss spatial index.

Setting the `all_tags` parameter to `true` will cause that once the tag is matched, the adjacent tags within the same element will be included in the resulting DataFrame.
