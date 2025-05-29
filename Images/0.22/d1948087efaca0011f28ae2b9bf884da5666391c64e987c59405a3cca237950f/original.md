```
ColorizedArray(intensity, label::IndirectArray) -> A
```

Create an array, combining a `label` array (where each pixel is assigned one of a list of discrete colors) and an `intensity` array (where each pixel has a scalar value). `A` satisfies

```
A[i,j,...] = intensity[i,j,...] * label[i,j,...]
```

The label array "tinges" the grayscale intensity with the color associated with that point's label.

This computation is performed lazily, as to be suitable even for large arrays.
