```
batch_matmul(o1::PyObject, o2::PyObject)
```

Computes `o1[i,:,:] * o2[i, :]` or `o1[i,:,:] * o2[i, :, :]` for each index `i`.
