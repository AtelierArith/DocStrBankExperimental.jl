```
recover_nearest(code, latitude, longitude)
```

Recover the nearest matching code to a specified location. Given a short code of between four and seven characters, this recovers the nearest matching full code to the specified location.

# Arguments:

  * `code`: A valid OLC character sequence.
  * `latitude`: The latitude (in signed degrees) to use to     find the nearest matching full code.
  * `longitude``: The longitude (in signed degrees) to use     to find the nearest matching full code.

# Returns:

The nearest full Open Location Code to the reference location that matches   the short code. If the passed code was not a valid short code, but was a   valid full code, it is returned with proper capitalization but otherwise   unchanged.
