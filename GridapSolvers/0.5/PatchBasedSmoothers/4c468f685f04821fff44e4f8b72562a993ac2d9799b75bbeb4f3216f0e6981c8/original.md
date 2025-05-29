```
struct PatchBasedLinearSolver <: LinearSolver
  ...
end
```

Sub-assembled linear solver for patch-based methods. Given a bilinear form `a` and a space decomposition `V = Σ_i V_i` given by a patch space, returns a global correction given by aggregated local corrections, i.e 

```
dx = Σ_i w_i I_i inv(A_i) (I_i)^* x 
```

where `A_i` is the patch-local system matrix defined by 

```
(A_i u_i, v_i) = a(u_i,v_i) ∀ v_i ∈ V_i
```

and `I_i` is the natural injection from the patch space to the global space. The aggregation can be un-weighted (i.e. `w_i = 1`) or weighted, where `w_i = 1/#(i)`.
