```
SDP(X_1)
```

Constructs an SDP optimization problem. 
NOTE: only elements of X_1 can be set for now. 
The SDP matrix is given by

$$
X = \begin{bmatrix}
    X_2  & X_1 \\
    X_1' & X_4
\end{bmatrix}
$$

# Parameters:

  * `X_1`: The block matrix X_1 of the SDP matrix X
