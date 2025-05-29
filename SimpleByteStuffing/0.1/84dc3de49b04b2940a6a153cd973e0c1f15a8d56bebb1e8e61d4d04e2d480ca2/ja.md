SimpleByteStuffingは、デバイスパケット通信のためのパケットを作成するために使用されます。

パケットを作成するには：

```
packet = create_packet({command}, {read_or_write}, {payload})

command: 8ビットコマンド
read_or_write: 許可される値は "READ" と "WRITE"
payload: 8ビットのベクター
```

受信したパケットを解析するには：

```
payload = parse_packet(packet)
```

```
packet: [SOP][CMD][Payload1][...][Payloadn][Checksum][EOP]
SOP - パケットの開始
CMD - 読み取り/書き込みビットを持つコマンド 
Payload - データ
Checksum - 8ビットのチェックサム
EOP - パケットの終了
```
