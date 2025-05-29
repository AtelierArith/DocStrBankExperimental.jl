`GetNameByKeyword(;keyword::String,api_key::String,page::Int=1)`

# Description

  * Search for name information based on a keyword.

# Parameters

  * `keyword`: The name keyword (at least 2 characters).
  * `api_key`: The API service key for registered users.
  * `page`: The page number, an integer not less than 1. If not provided, it defaults to 1.

# Results

  * `result`: A structure of type `GetNameByKeywordStruct`.
  * `result.data`: Dictionary converted from JSON information.
  * `result.count`: Total number of matches.
  * `result.page`: Current data page.
  * `result.limit`: Number of items displayed per page.
  * `result.abstract`: Refined data frame.

# Example

```
using SP2000China;
your_keyword="柳莺";
your_api_key = "Please register an account and obtain an API key";
your_page = 1;
result = GetNameByKeyword(keyword=your_keyword,api_key=your_api_key,page=your_page);
result.data
result.count
result.page
result.limit
result.abstract
```
