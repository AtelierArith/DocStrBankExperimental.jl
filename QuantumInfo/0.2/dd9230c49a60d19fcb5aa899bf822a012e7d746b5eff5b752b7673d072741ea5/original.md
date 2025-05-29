`ket`

Returns a vector corresponding to a particular basis unit vector in some Hilbert space.

The vector can be specified in a number of different ways:

  * by a string and a base
  * by a integer and a dimension

If the vector is specified by a string and a base, the dimension is inferred from the length of the string. The base is assumed to be 2 unless explicitly specified.

If the basis element is specified by an integer, the dimension is assumed to be 2 unless explicitly specified. The integer values allowed are 0 through the dimension minus 1.

Optionally, the type of the elements of the vector can be specified in the first argument.
