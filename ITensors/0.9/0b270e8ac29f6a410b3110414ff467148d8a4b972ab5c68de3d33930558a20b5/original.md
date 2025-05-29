```
dense(T::ITensor)
```

Make a new ITensor where the storage is the closest Dense storage, avoiding allocating new data if possible. For example, an ITensor with Diag storage will become Dense storage, filled with zeros except for the diagonal values.
