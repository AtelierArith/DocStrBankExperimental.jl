```
BlendColorDodge
```

The destination color is the result of dividing the backdrop color by the complementary color of the source color.

```
    if Cb == 0
        Cdest = 0
    elseif Csrc == 1
        Cdest = 1
    else
        Cdest = min(1, Cb / (1 - Csrc))
    end
```
