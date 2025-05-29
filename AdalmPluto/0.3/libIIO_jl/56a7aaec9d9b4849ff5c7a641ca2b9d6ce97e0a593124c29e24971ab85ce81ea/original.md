```
C_iio_device_set_data(device, data)
```

Associate a pointer to an iio_device structure. If the pointer is a Julia pointer, you need to protect the data from the GC.

See the [Julia Documentation](https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/#Garbage-Collection-Safety) and [`GC.@preserve`](https://docs.julialang.org/en/v1/base/base/#Base.GC.@preserve).

# Parameters

  * `device::Ptr{iio_device}` : A pointer to an iio_device structure
  * `data::Ptr{Cvoid}`        : A pointer to the data to be associated.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Device.html#gab566248f50503d8975cf258a1f218275)
