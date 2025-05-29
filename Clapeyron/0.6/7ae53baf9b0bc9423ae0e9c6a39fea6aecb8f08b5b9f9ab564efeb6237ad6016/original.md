```
get_k(model)::VarArg{Matrix}
```

Returns a matrix of "k-values" binary interaction parameters used by the input `model`. Returns `nothing` if the model cannot return the k-values matrix. In the case of multiple k-values (as is the case in T-dependent values, i.e: k(T) = k1 + k2*T), it will return a tuple of matrices corresponding to each term in the k-value expression. Note that some models do not store the k-value matrix directly, but they contain the value in an indirect manner. for example, cubic EoS store `a[i,j] = f(a[i],a[j],k[i,j])`, where `f` depends on the mixing rule.
