```
is_full(code)
```

Determine if a code is a valid full Open Location Code. Not all possible combinations of Open Location Code characters decode to valid latitude and longitude values. This checks that a code is valid and also that the latitude and longitude values are legal. If the prefix character is present, it must be the first character. If the separator character is present, it must be after four characters.
