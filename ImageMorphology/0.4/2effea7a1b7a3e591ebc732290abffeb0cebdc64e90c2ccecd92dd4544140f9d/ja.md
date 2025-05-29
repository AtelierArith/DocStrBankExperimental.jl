```
overbuild(marker, mask; [dims])
overbuild(marker, mask, se)
```

侵食による再構成。これは `op=erode` を用いた [`mreconstruct`](@ref mreconstruct) のエイリアスです。

インプレースバージョンの [`overbuild!`](@ref) や、双対演算子の [`underbuild`](@ref) も参照してください。
