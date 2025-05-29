```
C_iio_device_set_data(device, data)
```

iio_device 構造体へのポインタを関連付けます。ポインタが Julia ポインタである場合、GC からデータを保護する必要があります。

[Julia Documentation](https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/#Garbage-Collection-Safety) と [`GC.@preserve`](https://docs.julialang.org/en/v1/base/base/#Base.GC.@preserve) を参照してください。

# パラメータ

  * `device::Ptr{iio_device}` : iio_device 構造体へのポインタ
  * `data::Ptr{Cvoid}`        : 関連付けるデータへのポインタ。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gab566248f50503d8975cf258a1f218275)
