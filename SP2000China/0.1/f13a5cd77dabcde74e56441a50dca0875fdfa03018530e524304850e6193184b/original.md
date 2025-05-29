`GetSpeciesByCommonName(;common_name::String,api_key::String,page::Int=1)`

# Description

  * Query by common name and return species or subspecies information.

# Parameters

  * `common_name`: The common name, or a part of it.
  * `api_key`: The API service key for registered users.
  * `page`: The page number, an integer not less than 1. If not provided, it defaults to 1.

# Results

  * `result`: A structure of type `GetSpeciesByCommonNameStruct`.
  * `result.data`: Dictionary converted from JSON information.
  * `result.count`: Total number of matches.
  * `result.page`: Current data page.
  * `result.limit`: Number of items displayed per page.
  * `result.abstract`: Refined data frame.

# Example

```
using SP2000China;
your_common_name = "土人参";
your_api_key = "Please register an account and obtain an API key";
your_page = 1;
result = GetSpeciesByCommonName(common_name=your_common_name,api_key=your_api_key,page=your_page);
result.data
result.count
result.page
result.limit
result.abstract
```
