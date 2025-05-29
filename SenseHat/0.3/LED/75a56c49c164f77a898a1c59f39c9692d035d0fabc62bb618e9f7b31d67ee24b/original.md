```
led_matrix()
```

Returns an 8x8 matrix of `RGB565` elements that is memory-mapped to the Sense HAT LED Matrix.

While it is possible to invoke the function multiple times (each returning different arrays), it is generally preferable to assign it once into a `const` variable so as to minimise the number of open file handlers.

# Example

```
using SenseHat
using ColorTypes

const LED = led_matrix()

LED[:] = SenseHat.JULIA_LOGO
sleep(3)
LED[:] = RGB(0,0,0)
```
