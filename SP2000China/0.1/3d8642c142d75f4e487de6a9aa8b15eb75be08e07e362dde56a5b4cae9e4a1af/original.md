`GetFamiliesByFamilyName(;family_name::String,api_key::String,page::Int=1)`

# Description

  * Query by family name and return a collection of family IDs.

# Parameters

  * `family_name`: The family name, or a part of it, supporting both Latin and Chinese names.
  * `api_key`: The API service key for registered users.
  * `page`: The page number, an integer not less than 1. If not provided, it defaults to 1.

# Results

  * `result`: A structure of type `GetFamiliesByFamilyNameStruct`.
  * `result.data`: Dictionary converted from JSON information.
  * `result.count`: Total number of matches.
  * `result.page`: Current data page.
  * `result.limit`: Number of items displayed per page.
  * `result.abstract`: Refined data frame.

# Example

```
using SP2000China;
your_family_name = "Coriariaceae";
your_api_key = "Please register an account and obtain an API key";
your_page = 1;
result = GetFamiliesByFamilyName(family_name=your_family_name,api_key=your_api_key,page=your_page);
result.data
result.count
result.page
result.limit
result.abstract
```
