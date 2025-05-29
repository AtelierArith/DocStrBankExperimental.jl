normaliseangleaxis - Normalises angle-axis descriptor.

Function normalises theta so that it lies in the range -pi to pi to ensure one-to-one mapping between angle-axis descriptor and resulting rotation.

```
Usage: t2 = normaliseangleaxis(t)

Argument:   t  - 3-vector giving rotation axis with magnitude equal to the
                 rotation angle in radians.
Returns:    t2 - Normalised angle-axis descriptor
```

See also: matrix2angleaxis(), angleaxis(), angleaxis2matrix(), angleaxisrotate()
