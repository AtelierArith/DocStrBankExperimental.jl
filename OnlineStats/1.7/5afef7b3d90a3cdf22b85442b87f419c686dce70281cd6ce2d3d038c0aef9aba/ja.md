```
MovingWindow(b, T)
MovingWindow(T, b)
```

`T`型の`b`アイテムの移動ウィンドウを追跡します。円形バッファとも呼ばれます。

# 例

```
o = MovingWindow(10, Int)
fit!(o, 1:14)
```
