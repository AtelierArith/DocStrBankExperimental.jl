```
eachpoint(message::Message)
```

メッセージ内の各ポイントを反復処理し、lon、lat、および値を返します。

# 例

```Julia
for (lon, lat, val) in eachpoint(message)
    println("Value at ($lat, $lon) is $val")
end
```
