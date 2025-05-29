```
C_iio_channel_set_data(channel, data)
```

Associate a pointer to an iio_channel structure. If the pointer is a Julia pointer, you need to protect the data from the GC.

See the [Julia Documentation](https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/#Garbage-Collection-Safety) and [`GC.@preserve`](https://docs.julialang.org/en/v1/base/base/#Base.GC.@preserve).

# Parameters

  * `channel::Ptr{iio_channel}` : A pointer to an iio_channel structure
  * `data::Ptr{Cvoid}`          : The pointer to be associated.

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga5150c9b73386d899460ebafbe614f338)
