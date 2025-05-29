```
parse_dms(input)
```

Parses a string input in "deg:arcmin:arcsec" format to the tuple `(degrees, arcminutes, arcseconds)`. The following delimiters will all work and can be mixed together (the last delimiter is optional):

```
"[+-]xx[°d: ]xx['′m: ]xx[\"″s][NESW]"
```

if the direction is provided, "S" and "E" are considered negative (and "-1:0:0S" is 1 degree North)
