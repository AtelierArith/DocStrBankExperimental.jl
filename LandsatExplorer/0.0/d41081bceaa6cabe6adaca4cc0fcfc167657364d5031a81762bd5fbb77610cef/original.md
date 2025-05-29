```
authenticate(username, password)
```

Authenticate with your USGS Earth Explorer credentials.

Sets the environment variables `LANDSAT_EXPLORER_USER` and `LANDSAT_EXPLORER_PASS`, which will be used to authenticate future requests.

# Parameters

  * `username`: Your USGS Earth Explorer username.
  * `password`: Your USGS Earth Explorer password.

# Example

```julia
authenticate("my_username", "my_password")
```
