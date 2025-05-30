```
set_read_timeout(sp::SerialPort, seconds::Real)
```

`Timeout` 例外がスローされる前に、後で呼び出されるブロッキング読み取り関数が待機できる合計（累積）時間の読み取りタイムアウト制限を `t` > 0 秒に設定します。

# 例

```
sp=LibSerialPort.open("/dev/ttyUSB0", 115200)
# 2行が受信されるか
# 10秒が経過するまで待機
set_read_timeout(sp, 10)
try
    line1 = readuntil(sp, '\n')
    line2 = readuntil(sp, '\n')
catch e
    if isa(e, LibSerialPort.Timeout)
        println("遅すぎます！")
    else
        rethrow()
    end
end
clear_read_timeout(sp)
```

参照: [`clear_read_timeout`](@ref), [`set_write_timeout`](@ref)
