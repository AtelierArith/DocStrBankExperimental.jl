```
BlendColorBurn
```

宛先の色は、バックドロップの色の補色をソースの色で割った結果です。

ColorBlendModesは、以下に示すW3Cドラフトの定義を使用します。`Cb == 1`で`Csrc == 0`の場合に`0`を返すバリアントがあることに注意してください。

```
    if Cb == 1
        Cdest = 1
    elseif Csrc == 0
        Cdest = 0
    else
        Cdest = 1 - min(1, (1 - Cb) / Csrc)
    end
```
