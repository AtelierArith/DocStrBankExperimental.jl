```
in(b1::Rect, b2::Rect)
```

Rect `b1` が `b2` に含まれているかを確認します。これは厳密な不等式を使用しないため、Rect が面を共有していても、これが真を返すことがあります。
