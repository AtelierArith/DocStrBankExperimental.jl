```
get_l(model)::VarArg{Matrix}
```

returns a matrix of "l-values" binary interaction parameters used by the input `model`. Returns `nothing` if the model cannot return the l-values matrix. In the case of multiple l-values (as is the case in T-dependent values, i.e: l(T) = l1 + l2*T), it will return a tuple of matrices corresponding to each term in the l-value expression. Note that some models do not store the l-value matrix directly, but they contain the value in an indirect manner. for example, cubic EoS store `b[i,j] = f(b[i],b[j],l[i,j])`, where `f` depends on the mixing rule.
