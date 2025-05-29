```
sysi = innovation_form(sys, R1, R2[, R12])
sysi = innovation_form(sys; sysw=I, syse=I, R1=I, R2=I)
```

システムを取得します

```
x' = Ax + Bu + w ~ R1
y  = Cx + Du + e ~ R2
```

そしてシステムを返します

```
x' = Ax + Kv
y  = Cx + v
```

ここで `v` はイノベーションシーケンスです。

`sysw` (`syse`) が指定されている場合、`R1` (`R2`) を通じて `sysw` (`syse`) でフィルタリングノイズの結果として得られる共分散が共分散として使用されます。

確率制御、章4、Åströmを参照してください。
