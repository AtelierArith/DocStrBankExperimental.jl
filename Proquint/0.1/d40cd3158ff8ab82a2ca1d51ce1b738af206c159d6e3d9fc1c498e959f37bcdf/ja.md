# Proquints: 読みやすく、綴りやすく、発音しやすい識別子

これは、WilkersonのプロクイントのJulia実装であり、彼の論文[http://arXiv.org/html/0901.4016](http://arXiv.org/html/0901.4016)で説明されています。

要するに、16ビットは子音と母音を交互に配置した「プロクイント」として表現されます。

4ビットを子音として:

```
0 1 2 3 4 5 6 7 8 9 A B C D E F
b d f g h j k l m n p r s t v z
```

2ビットを母音として:

```
0 1 2 3
a i o u
```

全体の16ビットワード、ここで「con」は子音、「vo」は母音を表します:

```
 0 1 2 3 4 5 6 7 8 9 A B C D E F
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
|con    |vo |con    |vo |con    |
+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+-+
```

プロクイントはダッシュ `-` で区切られます。

## 短縮形 (拡張)

短縮形は16ビットワードの先頭のゼロをエンコードせず、全体のワードが0の場合は「x」としてエンコードされます。

## 例

`UInt32` `0x0a484904` はビット表現で次のようになります:

```
0000 10 1001 00 1000  0100 10 0100 00 0100
  b   o   n   a   m  -  h   o   h   a   h
      o   n   a   m  -  h   o   h   a   h   # 短縮版
```

IPアドレス `127.0.0.1` は `0x7f000001` `UInt32` です:

```
0111 11 1100 00 0000  0000 00 0000 00 0001
  l   u   s   a   b  -  b   a   b   a   d
  l   u   s   a   b  -                  d   # 短縮版
```

プロクイントは曖昧さがなく、整数から生成され、再び整数に変換できます:

```julia
julia> using Proquint

julia> uint2quint(0x7f000001)
"lusab-babad"

julia> uint2quint(0x7f000001, short=true) # これが短縮版を返します
"lusab-d"

julia> quint2uint("lusab-babad", UInt32)
0x7f000001

julia> quint2uint("lusab-d", UInt32)
0x7f000001
```
