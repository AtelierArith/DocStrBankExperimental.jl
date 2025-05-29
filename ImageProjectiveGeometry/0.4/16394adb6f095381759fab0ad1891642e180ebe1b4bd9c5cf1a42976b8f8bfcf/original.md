angleaxisrotate - Uses angle axis descriptor to rotate vectors

```
Usage: v2 = angleaxisrotate(t, v)

Arguments:  t  - 3-vector defining rotation axis and having magnitude 
                 equal to the rotation angle in radians.
            v  - 4xn matrix of homogeneous 4-vectors to be rotated or
                 3xn matrix of inhomogeneous 3-vectors to be rotated.
Returns:    v2 - The rotated vectors. 
```

See also: matrix2angleaxis(), angleaxis(), angleaxis2matrix(), normaliseangleaxis()
