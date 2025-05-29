`interpolate(x, yvalues, xrange)`

Returns the value of a function with input `x`, by linearly interpolating the function itself through the table `yvalues` and the range `xrange`. If `x` is out of the range, the value at the corresponding extremity is returned. This function corresponds to the `TABHL` function in the `DYNAMO` language. This latter function receives a table (that is, `yvalues`), a value (that is, `x`), a left and a right extreme of an interval (that is, `xrange`), and an increment value.
