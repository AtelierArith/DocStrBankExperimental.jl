```
 write_json(df::DataFrame, path::String;JSONObjectVector::Bool=true)

 Writes the contents of a DataFrame to a specified JSON file
```

# Arguments

  * `df::DataFrame`: The DataFrame containing the data to be written to a JSON file
  * `path::String`: Path to the local JSON file to be written
  * `JSONObjectVector::Bool`: Determines what JSON formatat to write, true means writing as a vector of JSON Objects, false writes as JSON arrays

# Examples

```
julia> df = DataFrame(A=1:5, B=["a", missing, "c", "d", "e"], C=[1.1, 2.2, 3.3, 4.4, 5.5]);

julia> write_json(df, "data.json")
```
