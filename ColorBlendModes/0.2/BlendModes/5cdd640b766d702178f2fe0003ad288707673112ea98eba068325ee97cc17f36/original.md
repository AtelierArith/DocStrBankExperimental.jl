```
BlendColorBurn
```

The destination color is the result of dividing the complementary color of the backdrop color by the source color.

ColorBlendModes uses the definition of W3C drafts as shown below. Note that there is a variant, which returns `0` when `Cb == 1` and `Csrc == 0`.

```
    if Cb == 1
        Cdest = 1
    elseif Csrc == 0
        Cdest = 0
    else
        Cdest = 1 - min(1, (1 - Cb) / Csrc)
    end
```
