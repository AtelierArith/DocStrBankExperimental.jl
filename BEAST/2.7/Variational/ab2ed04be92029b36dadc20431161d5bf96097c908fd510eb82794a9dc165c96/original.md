```
@varform <form-definition>
```

The Julia form compiler uses the Julia parser and meta-programming based traversal of the AST to create a structure containing all information required for the description of a variational formulation from an Expr that follows closely widespread mathematical convention.

E.g:

```
EFIE = @varform T[k,j] = e[k]
MFIE = @varform 0.5*I[k,j] + K[k,j] = h[k]
PMCH = @varform M[k,j] - η*T[k,m] + 1/η*T[l,j] + M[l,m] = e[k] + h[l]
```
