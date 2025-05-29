```
C_iio_channel_set_data(channel, data)
```

iio_channel 構造体へのポインタを関連付けます。ポインタが Julia ポインタである場合、GC からデータを保護する必要があります。

[Julia Documentation](https://docs.julialang.org/en/v1/manual/calling-c-and-fortran-code/#Garbage-Collection-Safety) と [`GC.@preserve`](https://docs.julialang.org/en/v1/base/base/#Base.GC.@preserve) を参照してください。

# パラメータ

  * `channel::Ptr{iio_channel}` : iio_channel 構造体へのポインタ
  * `data::Ptr{Cvoid}`          : 関連付けるポインタ。

[libIIO documentation](https://analogdevicesinc.github.io/libiio/master/libiio/group__Channel.html#ga5150c9b73386d899460ebafbe614f338)
