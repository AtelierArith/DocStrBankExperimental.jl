```
cambium_profile(; scenario::String, 
                            location_type::String, 
                            latitude::Real, 
                            longitude::Real,
                            start_year::Int,
                            lifetime::Int,
                            metric_col::String,
                            grid_level::String,
                            time_steps_per_hour::Int=1,
                            load_year::Int=2017,
                            profile_year::Int=2017,
                            )
```

This function constructs an API request to the Cambium database to retrieve either emissions data or clean energy fraction data depending on the `metric_col` provided. The data will be averaged on an hourly basis over the "lifetime" provided. The returned profiles are adjusted for day of week alignment with the provided "load_year" (Cambium profiles always start on a Sunday.)

This function is also used for the /cambium_profile endpoint in the REopt API, in particular for the webtool to display grid emissions data.
