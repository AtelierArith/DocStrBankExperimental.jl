```
Pi(; host = get(ENV, "PIGPIO_ADDR", ""),
   port = get(ENV, "PIGPIO_PORT", 8888))
```

PiのGPIOへのアクセスを許可します。

`host`は、pigpioデーモンが実行されているPiのホスト名です。デフォルトはlocalhostですが、PIGPIO_ADDR環境変数によって上書きされることがあります。

`port`は、pigpioデーモンがリッスンしているポート番号です。デフォルトは8888ですが、PIGPIO_PORT環境変数によって上書きされることがあります。pigpioデーモンは、同じポート番号で起動されている必要があります。

これはpigpioデーモンに接続し、コマンドを送信し通知を受信するために使用されるリソースを予約します。

インスタンス属性`connected`を使用して接続の成功を確認できます。接続が正常に確立されると`connected`はtrueになり、そうでない場合はfalseになります。

```julia
pi = PiGPIO.Pi()                           # デフォルトを使用
pi = PiGPIO.Pi(host = "mypi")              # ホストを指定、デフォルトポート
pi = PiGPIO.Pi(host = "mypi", port = 7777) # ホストとポートを指定

pi = PiGPIO.Pi()                           # 接続がない場合はスクリプトを終了
if !pi.connected
   exit()
end
```
