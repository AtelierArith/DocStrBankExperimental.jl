```
Geocoder(cities_data::AbstractDataFrame; filters::Vector{Function} = Function[])
Geocoder(;
    data_dir::String=DATA_DIR, 
    geo_file::String=GEO_FILE, 
    decoder_output_columns::Vector{Symbol} = DEFAULT_DECODER_OUTPUT,
    filters::Vector{Function} = Function[]
)
```

Geocoder structure that holds the reference points and their labels (city name and country code).

The second constructor is used to create the Geocoder from the geoname data that it automatically downloads on first run.
