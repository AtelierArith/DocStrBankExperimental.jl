`GetSpeciesByNameCode(;name_code::String,api_key::String)`

# Description

  * Retrieve detailed information based on the species ID.

# Parameters

  * `name_code`: The species ID.
  * `api_key`: The API service key for registered users.

# Results

  * `result`: A structure of type `GetSpeciesByNameCodeStruct`.
  * `result.data`: Dictionary converted from JSON information.
  * `result.abstract`: Refined data frame.

# Example

```
using SP2000China;
your_name_code = "1ac19d0d82d84dd2900d51a742fa9296";
your_api_key = "Please register an account and obtain an API key";
result = GetSpeciesByNameCode(name_code=your_name_code,api_key=your_api_key);
result.data
result.abstract
```
