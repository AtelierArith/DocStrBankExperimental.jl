```
filter_trajectories(collapsed_data::AbstractDataFrame, filter_settings::NamedTuple)
```

Filter out microbots that may be too small or large, going too slow, or stuck to the substrate.

The `filter_settings` is a `NamedTuple` with the following fields:

  * `MIN_VELOCITY` : minimum velocity in um/s
  * `MIN_BOUNDING_RADIUS` : minimum bounding radius in um
  * `MAX_BOUNDING_RADIUS` : maximum bounding radius in um
  * `MIN_DISPLACEMENT` : minimum total displacement in um

# Example

```julia
filter_settings = (
    MIN_VELOCITY = 10.0,  # um / s  
    MIN_BOUNDING_RADIUS = 3.38,  # um
    MAX_BOUNDING_RADIUS = 75,  # µm
    MIN_DISPLACEMENT = 0,  # µm
)

filtered_collapsed_data = filter_trajectories(collapsed_data, filter_settings)
```
