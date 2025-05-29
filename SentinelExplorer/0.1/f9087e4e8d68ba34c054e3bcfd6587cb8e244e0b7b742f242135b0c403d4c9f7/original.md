```
get_access_token()
get_access_token(username, password)
```

Receive a data access token with the provided credentials.

The username and password may be passed explicitly, or provided as a pair of environment variables.

In the case of the latter, `get_access_token()` expects your username and password to be provided as the  environment variables `SENTINEL_EXPLORER_USER` and `SENTINEL_EXPLORER_PASS`.

# Parameters

  * `username`: Your Copernicus Data Space username.
  * `password`: Your Copernicus Data Space password.

# Returns

An access token for downloading data.

# Example

```julia
token = get_access_token(ENV["SENTINEL_EXPLORER_USER"], ENV["SENTINEL_EXPLORER_PASS"])
token = get_access_token()  # Same as Above
```
