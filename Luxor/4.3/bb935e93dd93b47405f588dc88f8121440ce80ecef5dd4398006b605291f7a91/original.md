```
HueShift(t::Turtle, inc=1.0)
```

Shift the Hue of the turtle's pen by `inc`. Hue values range between 0 and 360.

If the turtle's `Pencolor` was "black" to start with, the saturation and brightness will be 0, so changing just the hue won't make a color that's easily distinguishable from black. The brightness and saturation of the new color will still be

0. 
