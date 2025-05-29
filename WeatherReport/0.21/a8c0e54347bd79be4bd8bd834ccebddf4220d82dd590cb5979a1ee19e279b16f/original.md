Saves the hourly historical temperature, rain, snowfall, relative humidity, windspeed and solar data for a given city (between "start*date" and "end*date") to a SQLite database. Each of the weather variable is saved as a separate table. The database itself is saved to the "export" folder in the root of this repository.

# Arguments

  * `city::String` : Valid city name, e.g. "Oslo", "Paris", "Amsterdam" etc.
  * `i_row::Int64` : In case of more than one match for a given location,                  select the desired timezone by providing the row index                  from the printed DataFrame. Default is set to 1.
  * `start_date::String` : Starting day in ISO8601 date format, e.g. "2023-02-01"
  * `end_date::String` : Ending day in ISO8601 date format, e.g. "2023-02-25"

# Optional keywords

  * `lat::Float64` : Geographical WGS84 coordinate of the location (°S < 0, °N > 0)
  * `long::Float64` : Geographical WGS84 coordinate of the location (°W < 0, °E > 0)

# Example

```julia-repl
julia> export_to_sqlite("Veldhoven", start_date = "2022-01-01", end_date = "2022-01-31")
```
