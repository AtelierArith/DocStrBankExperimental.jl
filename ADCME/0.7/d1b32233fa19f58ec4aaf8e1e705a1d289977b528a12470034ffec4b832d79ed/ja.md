```
batch_matmul(o1::PyObject, o2::PyObject)
```

`o1[i,:,:] * o2[i, :]` または `o1[i,:,:] * o2[i, :, :]` を各インデックス `i` に対して計算します。
