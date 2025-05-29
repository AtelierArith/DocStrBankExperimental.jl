```
noise(x)          ; detail = 1, persistence = 1.0) # 1D
noise(x, y)       ; detail = 1, persistence = 1.0) # 2D
noise(x, y, z)    ; detail = 1, persistence = 1.0) # 3D
noise(x, y, z, w) ; detail = 1, persistence = 1.0) # 4D
```

Generate a noise value between 0.0 and 1.0 corresponding to the `x`, `y`, `z`, and `w` values. An `x` value on its own produces 1D noise, `x` and `y` make 2D noise, and so on.

The `detail` value is an integer (>= 1) specifying how many octaves of noise you want.

The `persistence` value, typically between 0.0 and 1.0, controls how quickly the amplitude diminishes for each successive octave for values of `detail` greater than 1.
