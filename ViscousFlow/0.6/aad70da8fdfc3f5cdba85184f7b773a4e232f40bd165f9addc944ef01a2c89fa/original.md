```
moment(sol,sys,bodyi[;center=(0,0)]) -> Vector
```

Calculated the momemt exerted by the fluid on body `bodyi` from the computational solution `sol` of system `sys`. It returns the moment history as an array. The moment is calculated about center `center`, which defaults to `(0,0)` in whichever coordinate system the problem is solved.
