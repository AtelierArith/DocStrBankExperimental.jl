```
show_message(s::String, speed::Real = 0.2, color::ColorTypes.AbstractRGB = colorant"white")
```

`SenseHat` LEDマトリックスにスクロールメッセージ`s`を表示します。`speed`はフレームごとの時間（秒）で、`color`はテキストの色です。

# 例

```
using SenseHat

show_message("Hello, World!", 0.2, colorant"purple")
```
