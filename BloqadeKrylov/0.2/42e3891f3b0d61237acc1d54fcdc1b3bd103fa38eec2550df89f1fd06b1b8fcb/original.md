```
Compute a lower bound of the 1-norm of a matrix to a power of p

Parameters
----------
A : ndarray or other linear operator
    A linear operator that can be transposed and that can
    produce matrix products.
p : power of A, optional (default =1)
t : int, optional
    A positive parameter controlling the tradeoff between
    accuracy versus time and memory usage.
    Larger values take longer and use more memory
    but give more accurate output.
itmax : int, optional
    Use at most this many iterations.

Returns
-------
est : float
    An underestimate of the 1-norm of the sparse matrix.

Notes
-----
This is algorithm 2.4 of [1].

In [2] it is described as follows.
"This algorithm typically requires the evaluation of
about 4t matrix-vector products and almost invariably
produces a norm estimate (which is, in fact, a lower
bound on the norm) correct to within a factor 3."

.. versionadded:: 0.13.0

References
----------
.. [1] Nicholas J. Higham and Francoise Tisseur (2000),
       "A Block Algorithm for Matrix 1-Norm Estimation,
       with an Application to 1-Norm Pseudospectra."
       SIAM J. Matrix Anal. Appl. Vol. 21, No. 4, pp. 1185-1201.

.. [2] Awad H. Al-Mohy and Nicholas J. Higham (2009),
       "A new scaling and squaring algorithm for the matrix exponential."
       SIAM J. Matrix Anal. Appl. Vol. 31, No. 3, pp. 970-989.
```
