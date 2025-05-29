```
diagnose_match(X::Sheaf, cover, sections; debug=false)
```

For each object X in the diagram, check that all the sections restrict to the same value along the Hom(X, -).

The arguments haave the same interpretation as in `extend`.
