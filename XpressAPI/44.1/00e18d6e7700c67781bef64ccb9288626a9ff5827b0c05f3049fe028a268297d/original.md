```
XPRS_NAMELENGTH
```

The length (in 8 character units) of row and column names in the matrix. (integer)

To allocate a character array to store names, you must allow `8*NAMELENGTH+1` characters per name (the `+1` allows for the string terminator character).
