```
iirnotch(Wn, bandwidth[; fs])
```

Second-order digital IIR notch filter [^Orfandis] at frequency `Wn` with bandwidth `bandwidth`. If `fs` is not specified, `Wn` is interpreted as a normalized frequency in half-cycles/sample.

[^Orfandis]: Orfanidis, S. J. (1996). Introduction to signal processing. Englewood Cliffs, N.J: Prentice Hall, p. 370.
