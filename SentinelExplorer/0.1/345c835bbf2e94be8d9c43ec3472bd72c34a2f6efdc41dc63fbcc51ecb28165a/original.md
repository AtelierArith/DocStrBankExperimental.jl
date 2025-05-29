```
authenticate(username, password)
```

Authenticate with your Copernicus Data Space credentials.

Sets the environment variables `SENTINEL_EXPLORER_USER` and `SENTINEL_EXPLORER_PASS`, which will be used to authenticate future requests.

# Parameters

  * `username`: Your Copernicus Data Space username.
  * `password`: Your Copernicus Data Space password.

# Example

```julia
authenticate("my_username", "my_password")
token = get_access_token()
```
