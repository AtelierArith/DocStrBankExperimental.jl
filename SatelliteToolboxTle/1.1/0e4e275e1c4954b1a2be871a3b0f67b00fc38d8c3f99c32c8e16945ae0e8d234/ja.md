```
@tle_nc_str(str) -> TLE
```

文字列 `str` に含まれる1つのTLEを解析します。

この関数は、解析されたTLEを返すか、エラーが発生した場合は `nothing` を返します。

!!! note
    この関数は **TLEのチェックサムを** 検証しません。チェックサムの検証が必要な場合は、[`@tle_str`](@ref) を使用してください。


!!! note
    `str` には **1つのTLEのみ** が含まれている必要があります。したがって、2行または3行の非空行を持つ必要があります。`#` で始まる行は無視されます。


# 例

```julia-repl
julia> tles = tle_nc"""
       CBERS 4
       1 40336U 14079A   18166.15595376 -.00000014  00000-0  10174-4 0  9993
       2 40336  98.4141 237.7928 0001694  75.7582 284.3804 14.35485112184485
       """
```
