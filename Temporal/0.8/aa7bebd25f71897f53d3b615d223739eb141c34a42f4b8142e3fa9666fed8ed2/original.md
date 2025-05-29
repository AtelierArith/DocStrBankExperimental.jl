Set up Quandl user account authorization. Run once passing your Quandl API key, and it will be saved for future use.

```
quandl_auth(key::String=""; authfile::String=joinpath(homedir(),"quandl-auth"))::String
```
