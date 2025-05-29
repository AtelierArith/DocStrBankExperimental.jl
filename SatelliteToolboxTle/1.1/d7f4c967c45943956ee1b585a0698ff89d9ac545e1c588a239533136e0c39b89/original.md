```
tle_line_checksum(str::AbstractString) -> Int
```

Compute the checksum of the line `str` modulo 10.

The algorithm is simple: add all the numbers in the line, ignoring letters, spaces, periods, and plus signs, but assigning +1 to the minus signs. The checksum is the remainder of the division by 10.
