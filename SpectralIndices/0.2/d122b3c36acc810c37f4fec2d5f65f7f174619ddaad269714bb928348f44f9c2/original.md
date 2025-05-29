```
load_json(file::String = "spectral-indices-dict.json")
```

Load a specified JSON file from the `data` folder.

# Arguments

  * `file::String = "spectral-indices-dict.json"`: The name of the JSON file to be loaded.

# Returns

  * `object`: The parsed JSON content from the specified file.

# Examples

```julia
# Load the default JSON file
data = load_json()

# Load a specific JSON file
data = load_json("my-custom-indices.json")
```
