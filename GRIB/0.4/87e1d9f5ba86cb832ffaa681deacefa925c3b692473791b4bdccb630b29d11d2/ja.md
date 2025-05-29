```
data(handle::Message)
```

メッセージから経度、緯度、および値を取得します。

# 例

```
GribFile(filename) do f
    msg = Message(f)
    lons, lats, values = data(msg)
end
```
