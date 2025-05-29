```
fixdatevec!(dateVec)
```

Adjust a date vector to account for out of bounds conditions.

For example, [2024., 5, 32, 0, 0, 0] will be adjusted to [2024., 6, 1, 0, 0, 0]

Currently accounts for leap years but not leap seconds. May still have issues if required to cross multiple leap years.
