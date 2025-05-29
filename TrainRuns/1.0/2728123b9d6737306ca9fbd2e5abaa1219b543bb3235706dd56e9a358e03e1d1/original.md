```
Path(characteristic_sections::DataFrame)
```

Path is a datastruture for calculation context. The function Path() will create a running path for the train. Optional arguments:     * points*of*interest::DataFrame # Points of interest

```
Path(characteristic_sections::DataFrame, points_of_interest::DataFrame)
```

Keyword Arguments:     * name::String     * id::String     * uuid::UUID

characteristic*sections DataFrame needs the following columns:     * :position,     * :speed,     * :resistance points*of_interest (poi) DataFrame needs the following columns:     * :position,     * :label,     * :measure

# Example

```
julia> my_path = Path(characteristic_sections) # will generate a path from a DataFrame.
Path(variables)
```
