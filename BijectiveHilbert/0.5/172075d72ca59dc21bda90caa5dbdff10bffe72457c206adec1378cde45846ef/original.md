```
GlobalGray(b, n)
GlobalGray(T, b, n)
```

`T` is a data type for the Hilbert index. It can be signed or unsigned, as long as it has at least `n * b` bits. `n` is the number of dimensions, and `b` is the bits per dimension, so each axis value should be between 0 and $2^b - 1$, inclusive, for the zero-based interface. They should be between 1 and $2^b$, inclusive, for the one-based interface.

The GlobalGray algorithm is an n-dimensional Hilbert curve with a simplified implementation. It follows an article, "Programming the Hilbert Curve," by John Skilling, 707 (2004), http://dx.doi.org/10.1063/1.1751381. I call it "Global Gray" because the insight of the article is that a single, global Gray code can be applied to all np bits of a Hilbert length.
