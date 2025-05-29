```
underbuild(marker, mask; [dims])
underbuild(marker, mask, se)
```

膨張による再構成。これは `op=dilate` を用いた [`mreconstruct`](@ref mreconstruct) のエイリアスです。

インプレースバージョンの [`underbuild!`](@ref) や、双対演算子の [`overbuild`](@ref) も参照してください。
