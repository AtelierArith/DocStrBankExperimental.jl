```
extract_result(r::Result, ops::NTuple{N,Outfun}) --> Row Matrix
extract_result(r::AbstractVector{Result}, ops::NTuple{N,Outfun}) --> Matrix
```

Return a matrix of outputs extracted from a `Result` instance or vector.  `ops` is a  `NTuple` as returned by the `@outputs` macro.

### Example

```
results = analyze(...)
ops = @outputs FGHz s11dB(h,h) s11ang(h,h)
data = extract_result(results, ops)
# or data = extract_result(results[1], ops) # returns a single row
```
