```
led_matrix()
```

`RGB565` 要素の 8x8 マトリックスを返し、Sense HAT LED マトリックスにメモリマップされています。

関数を複数回呼び出すことは可能ですが（それぞれ異なる配列を返します）、一般的には `const` 変数に一度割り当てて、オープンファイルハンドラの数を最小限に抑えることが好ましいです。

# 例

```
using SenseHat
using ColorTypes

const LED = led_matrix()

LED[:] = SenseHat.JULIA_LOGO
sleep(3)
LED[:] = RGB(0,0,0)
```
