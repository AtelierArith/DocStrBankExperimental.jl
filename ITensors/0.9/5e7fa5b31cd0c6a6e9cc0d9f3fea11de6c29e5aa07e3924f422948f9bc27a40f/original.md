```
transpose(T::ITensor)
```

Treating an ITensor as a map from a set of indices of prime level 0 to a matching set of indices but of prime level 1 [for example: (i,j,k,...) -> (j',i',k',...)] return the ITensor which is the transpose of this map.
