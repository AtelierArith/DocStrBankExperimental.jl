```
set_write_timeout(sp::SerialPort, seconds::Real)
```

`Timeout` 例外がスローされる前に、後で呼び出されるブロッキング読み取り関数が待機できる合計（累積）時間の書き込みタイムアウト制限を `t` > 0 秒に設定します。

# 例

```
sp=LibSerialPort.open("/dev/ttyUSB0", 300)
# シリアルポートドライバに4000期間が
#渡されるか、10秒が経過するまで待機
set_write_timeout(sp, 10)
try
    for i=1:50 ; write(sp, '.' ^ 80); end
catch e
    if isa(e, LibSerialPort.Timeout)
        println("これは時間がかかりすぎました！")
    else
        rethrow()
    end
end
clear_write_timeout(sp)
```

参照: [`clear_write_timeout`](@ref), [`set_read_timeout`](@ref)
