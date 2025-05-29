```
join_multicast_group(sock::UDPSocket, group_addr, interface_addr = nothing)
```

特定のマルチキャストグループを `group_addr` で定義されたソケットに参加させます。 `interface_addr` が指定されている場合は、マルチホーミングシステムの特定のインターフェースを指定します。 グループの受信を無効にするには `leave_multicast_group()` を使用します。
