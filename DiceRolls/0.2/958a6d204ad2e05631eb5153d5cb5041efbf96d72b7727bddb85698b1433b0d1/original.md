```
@roll_str(str)
```

Convenient string macro. Format: <n rolls>#<N>d<faces>+<modifier><mod effect>

<n rolls>, <N>, <modifier>, <mod effect> are optional.

Example:

```
r"2#1d20+6" # Rolls 1d20+6 twice
r"2d20kh1" # Rolls 2d20 and keeps highest
```
