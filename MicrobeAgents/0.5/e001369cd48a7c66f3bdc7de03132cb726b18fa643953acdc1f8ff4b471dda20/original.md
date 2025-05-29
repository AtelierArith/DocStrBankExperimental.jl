```
microbe_step!(microbe, model)
```

Perform an integration step for `microbe`. In order:

1. Update `microbe` position according to its current velocity
2. Reorient `microbe` through rotational diffusion
3. Update internal state of `microbe` through a customizable `affect!` function
4. Reorient `microbe` (if the motile state has a reorientation component)
5. Update motile state of microbe (transitions occur as Poisson events)
