```
GrB_finalize()
```

`GrB_finalize` は最後の GraphBLAS 操作として呼び出さなければなりません。`GrB_finalize` は `GrB_wait` を呼び出さず、保留中の計算は放棄されます。
