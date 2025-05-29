```
translate_to!(molecule, xf)
translate_to!(molecule, x)
translate_to!(molecule, xf, box)
translate_to!(molecule, x, box)
```

Translate a molecule so that its center of masss is at a point `xf` in fractional coordinate space or at `x` in Cartesian coordinate space. For the latter, a unit cell box is required for context.
