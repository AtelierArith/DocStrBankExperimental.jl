`LibSerialPort`モジュールは、ポータブルCライブラリ[libserialport](http://sigrok.org/wiki/Libserialport)を使用して、[シリアルポート](https://en.wikipedia.org/wiki/Serial_port)（[UART](https://en.wikipedia.org/wiki/Universal_asynchronous_receiver-transmitter)またはそのオペレーティングシステムインターフェースをエミュレートするUSB/Bluetoothデバイス）へのアクセスを提供します。

このモジュールは、`LibSerialPort.open`によって返される`SerialPort`型を定義しています。これは`Base.IO`のサブタイプであり、したがって、`Base.IO`に対して定義されている多くの同じ`read`、`write`、`print`などのメソッドを使用して、ファイルハンドルのように使用できます。

# 例

```
using LibSerialPort

list_ports()
ports = get_port_list()

sp = LibSerialPort.open("/dev/ttyUSB0", 115200)
set_flow_control(sp)
sp_flush(sp, SP_BUF_BOTH)
write(sp, "hello\n")
println(readline(sp))
close(sp)
```
