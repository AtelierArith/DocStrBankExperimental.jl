```
cubic_shell_embedding(s, γ, τ, B, k, bc=PeriodicBoundary()) → embedding
```

Create a [`SpatioTemporalEmbedding`](@ref) instance that includes spatial neighbors in hypercubic *shells*. The embedding is to be used with data from `s`.

## Description

Points are participating in the embedding by forming hypercubic shells around the current point. The total shells formed are `B`. The points on the shells have spatial distance `k ≥ 1` (distance in indices, like a cityblock metric). `k = 1` means that all points of the shell participate. The points of the hypercubic grid can be separated by `k ≥ 1` points apart (i.e. dropping `k-1` in-between points). In short, in each spatial dimension of the system the cartesian offset indices are `-B*k : k : k*B`.

`γ` is the number of temporal steps in the past to be included in the embedding, where each step in the past has additional delay time `τ::Int`. `γ=0` corresponds to using only the present. Notice that **all** embedded time frames have the same spatial structure, in contrast to [`light_cone_embedding`](@ref).

As an example, consider one of the `γ` embedded frames (all are the same) of a system with 2 spatial dimensions (`□` = current point, (included *by definition* in the embedding), `n` = included points in the embedding coming from `n`-th shell, `.` = points not included in the embedding)

```
      B = 2,  k = 1        |        B = 1,  k = 2        |        B = 2,  k = 2
                           |                             |
.  .  .  .  .  .  .  .  .  |  .  .  .  .  .  .  .  .  .  |  2  .  2  .  2  .  2  .  2
.  .  .  .  .  .  .  .  .  |  .  .  .  .  .  .  .  .  .  |  .  .  .  .  .  .  .  .  .
.  .  2  2  2  2  2  .  .  |  .  .  1  .  1  .  1  .  .  |  2  .  1  .  1  .  1  .  2
.  .  2  1  1  1  2  .  .  |  .  .  .  .  .  .  .  .  .  |  .  .  .  .  .  .  .  .  .
.  .  2  1  □  1  2  .  .  |  .  .  1  .  □  .  1  .  .  |  2  .  1  .  □  .  1  .  2
.  .  2  1  1  1  2  .  .  |  .  .  .  .  .  .  .  .  .  |  .  .  .  .  .  .  .  .  .
.  .  2  2  2  2  2  .  .  |  .  .  1  .  1  .  1  .  .  |  2  .  1  .  1  .  1  .  2
.  .  .  .  .  .  .  .  .  |  .  .  .  .  .  .  .  .  .  |  .  .  .  .  .  .  .  .  .
.  .  .  .  .  .  .  .  .  |  .  .  .  .  .  .  .  .  .  |  2  .  2  .  2  .  2  .  2
```
