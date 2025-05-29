```
shorten(code, latitude, longitude)
```

Remove characters from the start of an OLC code. This uses a reference location to determine how many initial characters can be removed from the OLC code. The number of characters that can be removed depends on the distance between the code center and the reference location.

The minimum number of characters that will be removed is four. If more than four characters can be removed, the additional characters will be replaced with the padding character. At most eight characters will be removed. The reference location must be within 50% of the maximum range. This ensures that the shortened code will be able to be recovered using slightly different locations.

# Arguments

  * `code`: A full, valid code to shorten.
  * `latitude`: A latitude, in signed degrees, to use as the reference point.
  * `longitude`: A longitude, in signed degrees, to use as the reference point.

# Returns:

Either the original code, if the reference location was not close enough,   or the shortest code which can be used to recover from the reference location.
