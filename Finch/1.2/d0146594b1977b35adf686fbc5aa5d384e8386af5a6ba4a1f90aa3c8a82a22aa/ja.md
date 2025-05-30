parallel(ext, device=CPU(nthreads()), schedule=static_schedule())

`ext`という次元が`device`上で`schedule`を使用して並列化されます。`ext`フィールドは通常`_`または次元のないものでありますが、標準の次元引数のいずれかであることもできます。
