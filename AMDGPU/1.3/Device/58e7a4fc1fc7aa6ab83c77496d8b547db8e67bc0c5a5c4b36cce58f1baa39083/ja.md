```
ROCDeviceArray(dims, ptr)
ROCDeviceArray{T}(dims, ptr)
ROCDeviceArray{T,A}(dims, ptr)
ROCDeviceArray{T,A,N}(dims, ptr)
```

`N`次元の密なROCデバイス配列を要素型`T`で構築し、ポインタをラップします。ここで、`N`は`dims`の長さから決定され、`T`は`ptr`の型から決定されます。`dims`は単一のスカラーまたは各次元の長さに対応する整数のタプルである可能性があります。ランク`N`が`Array{T,N}(dims)`のように明示的に指定されている場合、それは`dims`の長さと一致しなければなりません。同様に、要素型`T`もポインタ`ptr`の型と一致する必要があります。
