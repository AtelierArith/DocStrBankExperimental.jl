```
Bonding
```

Selection mode for the detection of bonds. The choices are:

  * `Input`: use the input bonds. Fail if those are not specified.
  * `Guess`: guess bonds using a variant of chemfiles / VMD algorithm.
  * `Auto`: if the input specifies bonds, use them unless they look suspicious (too small or or too large according to a heuristic). Otherwise, fall back to `Guess`.
  * `NoBond`: do not guess or use any bond. This cannot be used to determine topology.
