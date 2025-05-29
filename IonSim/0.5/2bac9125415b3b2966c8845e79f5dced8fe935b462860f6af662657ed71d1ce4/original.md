```
clearsublevelalias!(I::Ion, sublevel)
```

Erases the assignment of an alias to `sublevel` of Ion `I`. Accepts either the full sublevel `Tuple{String,Real}` or its alias `String`. Also accepts a vector of sublevels to clear multiple alias assignments in a single call.
