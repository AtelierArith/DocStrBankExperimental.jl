```
extract_result(fname::AbstractString, ops::Tuple) --> Matrix
```

Return a matrix of outputs extracted from a results file.  `ops` is a  Tuple returned by the `@outputs` macro.

### Example

```
ops = @outputs FGHz S11DB(H,H) S11ANG(H,H)
data = extract_result("pssfss.res", ops)
```
