```
extract_countries([geotable::GeoTables.GeoTable]; skip_areas = nothing, kwargs...)
extract_countries(admin::Union{AbstractString, Vector{<:AbstractString}}; skip_areas = nothing, kwargs...)
```

Extract and returns the domain (`<:Meshes.Domain`) containing all the countries that match a search query provided via the kwargs...

The returned `domain` can be used to check inclusion of points expressed as [`SimpleLatLon`](@ref) instances, or can be directly plotted using `scattergeo` from PlotlyBase and the dependent packages (e.g. PlutoPlotly, PlotlyJS)

The function can take as input a custom `geotable` but it's usually simply called without one, in which case it uses the one loaded by default by the package, which is obtained from the 1/110m maps from [naturalearthdata.com](https://www.naturalearthdata.com/).  Specifically, the shape file used to obtain the coordinates of the countries borders is located at [https://github.com/nvkelso/natural-earth-vector/blob/ca96624a56bd078437bca8184e78163e5039ad19/geojson/ne*110m*admin*0*countries_lakes.geojson](https://github.com/nvkelso/natural-earth-vector/blob/ca96624a56bd078437bca8184e78163e5039ad19/geojson/ne_110m_admin_0_countries_lakes.geojson)

The `geotable` contains a row per country and various country-related informations among the columns

The downselection of countries to form a domain is performed by passing keyword arguments containing `String` or `Vector{String}` values. 

# Extended Help

## Input Parsing

For each keyword argument, the function performs a downselection on the `geotable` column whose name matches the keyword argument name. The downselection is done based on the string provided as value:

  * The string is used to match the full name (case-insensitive) with the value of the specified column for each row of the table.
  * The `*` wildcard can be used within the string to expand to any number of word or space characters.
  * If the string starts with the '-' character, all rows that match are removed from the current downselection. Otherwise, the matching rows are added to the downselection (One can also put a '+' in front of the string to use for the matching to emphasise addition rather than deletion).
  * Multiple query/match strings can also be provided for each keyword argument, either as a vector of strings or within the same string but separated by ';'

      * The multiple queries are processed in the order they are provided, adding or removing to the total downselection accordingly
  * Each keyword argument is processed in the order it was provided, also modifying the downselection as described in the previous points.
  * The name of the keyword argument is made all uppercase before matching with the column names of `shapefile`, as the column names for the default table are all uppercase, so calling `extract_countries(;ConTinEnt = "Asia")` will match against the `:CONTINENT` column of the `shapefile`.

### Parsing Examples

  * `extract_countries(;continent = "europe", admin="-russia")` will extract the borders of all countries within the european continent except Russia
  * `extract_countries(;admin="-russia", continent = "europe")` will extract the borders of all countries within the european continent **including** Russia. This is because the strings are processed in order, so Russia is first removed and then Europe (which includes Russia) is added.
  * `extract_countries(;subregion = "*europe; -eastern europe")` will extract all countries that have a `subregion` name ending with `europe` (That is northern, eastern, western and southern) but will not include countries within the `eastern europe` subregion.

For a list of possible column names, call the function `CountriesBorders.valid_column_names()`.

For a list of the possible values contained in the table for some of the most useful colulmn names, call the function `CountriesBorders.possible_selector_values()`.

## Skipping Areas

Apart from removing areas with the string parsing synthax detailed above, one can also provide a list of countries (basd on the `ADMIN` name) or subareas of countries by using the `skip_area` keyword argument.

The provided `skip_area` must be an array of elements that can be:

  * instances of `SkipDict`
  * instances of `SkipFromAdmin`
  * instances of objects that can be used directly to construct `SkipFromAdmin` objects:

      * A single `String`. (will translate to a `SkipFromAdmin` with the provided `String` as `admin` and the Colon (:) as second argument)
      * instances `t` of `Tuple{<:AbstractString, <:Any}`, in which case the resulting `SkipFromAdmin` will be created as `SkipFromAdmin(t...)`

The provided elements will be merged into a single list of countries/areas to skip which will be removed from the nominal output of `extract_countries`.

A default set of Non-continental EU areas to skip is available in the exported constant `SKIP_NONCONTINENTAL_EU` which can be passed as the `skip_areas` argument (or as one of the elements of the array passed to `skip_areas`).

### Example

```jldoctest
julia> using CountriesBorders

julia> dmn = let
        # The following code will extract the borders of Italy, France and Norway without French Guyana (part of France), without Sicily, and without the Svalbard Islands (part of Norway)
        extract_countries("italy; spain; france; norway"; skip_areas = [
            ("Italy", 2) # This removes the second polygon in the Italy MultiPolyArea, which corresponds to Sicily
            "Spain" # This will remove Spain in its entirety
            SKIP_NONCONTINENTAL_EU # This will remove Svalbard and French Guyana
        ])
       end
3 view(::GeometrySet{CountryBorder{Float32}}, resolution = 110m, [22, 44, 142])
├─ Norway (3 skipped)
├─ France (1 skipped)
└─ Italy (1 skipped)

julia> catania = LatLon(37.5, 15.09) # Location of Catania, Sicily
GeodeticLatLon{WGS84Latest} coordinates
├─ lat: 37.5°
└─ lon: 15.09°

julia> Point(catania) in dmn # This returns false, as sicily is excluded from the domain
false

julia> rome = LatLon(41.9, 12.49) # Rome
GeodeticLatLon{WGS84Latest} coordinates
├─ lat: 41.9°
└─ lon: 12.49°

julia> Point(rome) in dmn # This returns true
true
```
