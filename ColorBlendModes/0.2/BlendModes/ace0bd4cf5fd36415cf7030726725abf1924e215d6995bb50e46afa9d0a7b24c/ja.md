```
BlendColorDodge
```

宛先の色は、バックドロップの色をソースの補色で割った結果です。

```
    if Cb == 0
        Cdest = 0
    elseif Csrc == 1
        Cdest = 1
    else
        Cdest = min(1, Cb / (1 - Csrc))
    end
```
