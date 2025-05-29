hnormalise - 同次座標の配列をスケール1に正規化します

```
Usage:  nx = hnormalise(x)

Argument:
        x  - 同次座標のNxnpts配列。

Returns:
        nx - スケール値nx[end,:]がすべて1になるように再スケールされた
             同次座標のNxnpts配列。
```

無限大の同次座標（スケール値が0のもの）は変更されません。

関連: hnormalise!()
