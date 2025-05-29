```
set_off_diag_constraint(sdp, data, mask)
```

Set the off diagonal entries in the SDP matrix. i.e. [Y data; data' Z] The mask is a boolean matrix that corresponds to which elements of the data matrix to keep.

### Output

The precomputed matrices A, G and the vector b to pass as arguments to ConeQP.
