```
XPRS_ETATOL
```

Tolerance on eta elements. (double)

During each iteration, the basis inverse is premultiplied by an elementary matrix, which is the identity except for one column - the eta vector. Elements of eta vectors whose absolute value is smaller than `ETATOL` are taken to be zero in this step.

Default value: `1.0E-13`

Domain: (0,+INF]
