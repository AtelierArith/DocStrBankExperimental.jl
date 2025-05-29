Interpolation matrix

Often it is necessary to compute the values of a function approximated using Lagrange interpolation through a set of points `z`. If this will be repeated often, a matrix can be computed that allows the easy computation using the simple expression `fx = Imat * fz`
