```
hemispheric_functions(A::ClimArray) → north, south
```

Return two arrays `north, south`, by splitting `A` to its northern and southern hemispheres, appropriately translating the latitudes of `south` so that both arrays have the same latitudinal dimension (and thus can be compared and do opperations between them).
