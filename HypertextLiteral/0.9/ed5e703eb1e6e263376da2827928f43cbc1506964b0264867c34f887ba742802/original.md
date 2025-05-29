```
@htl string-expression
```

Create a `Result` object with string interpolation (`$`) that uses context-sensitive hypertext escaping. Before Julia 1.6, interpolated string literals, e.g. `$("Strunk & White")`, are treated as errors since they cannot be reliably detected (see Julia issue #38501).
