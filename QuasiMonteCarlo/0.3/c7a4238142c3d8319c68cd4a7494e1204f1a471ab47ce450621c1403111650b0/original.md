```
randomize(x, R::ScrambleMethod)
```

Return a scrambled version of `x`. The scramble methods implemented are

  * `DigitalShift`.
  * `OwenScramble`: Nested Uniform Scramble which was introduced in Owen (1995).
  * `MatousekScramble`: Linear Matrix Scramble which was introduced in Matousek (1998).
