Download time series data from Quandl as a TS object.

```
quandl(code::String;
       from::String="",
       thru::String="",
       freq::Char='d',
       calc::String="none",
       sort::Char='a',
       rows::Int=0,
       auth::String=quandl_auth())::TS
```

# Arguments

  * `code::String;`: quandl code to query
  * `from::String=""`: start date from which the data should begin, expressed as a string of format yyyy-mm-dd
  * `thru::String=""`: end date through which the data should continue, expressed as a string of format yyyy-mm-dd
  * `freq::Char='d'`: frequency at which the data should occur (one of 'd', 'w', 'm', 'q', or 'a')
  * `calc::String="none"`: the calculation passed through to the Quandl engine (one of "none", "diff", "rdiff", "cumul", or "normalize")
  * `sort::Char='a'`: direction in which to sort results (one of 'a' or 'd')
  * `rows::Int=0`: number of rows to return from query (default corresponds to all rows)
  * `auth::String=quandl_auth()`: authorization token for the Quandl API dedicated to a user account
