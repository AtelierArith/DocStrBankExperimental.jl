```
RedPitaya(ip [, port = 5025, dataPort=5026, isMaster = false])
```

`RedPitaya`を構築します。

構築中に接続が確立され、RedPitayaのEEPROMからキャリブレーション値が読み込まれます。接続を試みている間にタイムアウトが発生した場合はエラーがスローされます。

# 例

```julia
julia> rp = RedPitaya("192.168.1.100");

julia> decimation!(rp, 8)
true

julia> decimation(rp)
8
```
