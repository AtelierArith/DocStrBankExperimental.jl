```
normalize(q)
```

Return a copy of this quaternion, normalized.

Note that this returns the same type as the input quaternion.  If you want to convert to a `Rotor`, just call `rotor(q)`, which includes a normalization step.
