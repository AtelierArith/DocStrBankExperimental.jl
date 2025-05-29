```
is_valid(code::AbstractString)
```

Determine if a code is valid. To be valid, all characters must be from the Open Location Code character set with at most one separator. The separator can be in any even-numbered position up to the eighth digit.
