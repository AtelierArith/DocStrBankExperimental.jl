```
simplify_fractions(x; polyform=false)
```

Find `Div` nodes and simplify them by cancelling a set of factors of numerators and denominators. If `polyform=true` the factors which were converted into PolyForm for the purpose of finding polynomial GCDs will be left as they are. Note that since PolyForms have different `hash`es than SymbolicUtils expressions, `substitute` may not work if `polyform=true`
