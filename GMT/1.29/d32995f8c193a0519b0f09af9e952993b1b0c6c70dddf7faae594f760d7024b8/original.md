```
isnodata(array::AbstractArray, val=0)
```

Return a boolean array with the same size a `array` with 1's (`true`) where $array[i] == val$. Test with an image have shown that this function was 5x faster than $ind = (I.image .== 0)$
