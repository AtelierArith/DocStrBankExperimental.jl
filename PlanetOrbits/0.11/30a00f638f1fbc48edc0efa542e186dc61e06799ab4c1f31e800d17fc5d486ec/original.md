```
Visual{OrbitType}(..., plx=...)
```

This wraps another orbit to add the parallax distance field `plx`, thus allowing projected quantities to be calculated. It forwards everything else to the parent orbit.

For example, the KepOrbit type supports calculating x and y positions in AU. A Visual{KepOrbit} additionally supports calculating projected right ascension and declination offsets.

!!! note
    The `ThieleInnesOrbit` type does not need to be wrapped in `Visual` as it the Thiele-Innes constants are already expressed in milliarcseconds and thus it always requires a `plx` value.

