```
Y = Weingarten(TpM::TangentSpace, X, V, A)
Weingarten!(TpM::TangentSpace, Y, p, X, V)
```

Compute the Weingarten map $\mathcal W_X$ at `X` on the [`TangentSpace`](@ref) `TpM` with respect to the tangent vector $V \in T_p\mathcal M$ and the normal vector $A \in N_p\mathcal M$.

Since this a flat space by itself, the result is always the zero tangent vector.
