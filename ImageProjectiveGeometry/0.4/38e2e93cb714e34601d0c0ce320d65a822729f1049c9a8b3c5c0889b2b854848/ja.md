hnormalise! - 同次座標をスケール1に正規化するインプレース操作

```
Usage:   hnormalise!(x)

Argument:
        x - 同次座標のNxnpts配列。

Return value and side effect:
        x - xの同次座標は再スケーリングされ、
            スケール値x[end,:]がすべて1になります。
```

無限大の同次座標（スケール値が0のもの）は変更されないことに注意してください。

関連: hnormalise()
