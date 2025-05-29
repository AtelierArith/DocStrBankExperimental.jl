```
spatialproperties(img)
```

Return a vector of strings, containing the names of properties that have been declared "spatial" and hence should be permuted when calling `permutedims`.  Declare such properties like this:

```
img[:spatialproperties] = [:spacedirections]
```
