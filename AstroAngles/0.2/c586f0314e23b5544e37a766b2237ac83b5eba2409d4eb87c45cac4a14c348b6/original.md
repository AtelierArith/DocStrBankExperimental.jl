```
parse_hms(input)
```

Parses a string input in "ha:min:sec" format to the tuple `(hours, minutes, seconds)`. The following delimiters will all work and can be mixed together (the last delimiter is optional):

```
"[+-]xx[h ]xx['′m: ]xx[\"″s][EW]"
```

if the direction is provided, "S" and "E" are considered negative (and "-1:0:0W" is 1 degree East)
