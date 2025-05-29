```
nni!(αu::Edge, u::Node, uv::Edge, v::Node, vδ::Edge)
nni!(αu,u,uv,v,vδ, flip::Bool, inner::Bool, indices)
```

Transform a network locally around the focus edge `uv` with the following NNI, that detaches u-β and grafts it onto vδ:

```
α - u -- v ------ δ
    |    |
    β    γ

α ------ v -- u - δ
         |    |
         γ    β
```

`flip` boolean indicates if the uv edge was flipped `inner` boolean indicates if edges αu and uv both point toward node u, i.e. α->u<-v<-δ. If this is true, we flip the hybrid status of αu and vδ.

`indices` give indices for nodes and edges u*in*αu, αu*in*u, vδ*in*v, and v*in*vδ. These are interpreted as:

```
u_in_αu: the index for u in the edge αu
αu_in_u: the index for αu in node u
vδ_in_v: the index for vδ in node v
v_in_vδ: the index for v in edge vδ
```

**Warnings**:

  * *No* check of assumed adjacencies
  * Not implemented for cases that are not necessary thanks to symmetry, such as cases covered by `nni!(vδ, v, uv, u, αu)` or `nni!(βu, u, v, vγ)`. More specifically, these cases are not implemented (and not checked):

      * u not hybrid & v hybrid
      * u hybrid, v not hybrid, α -> u <- v -> δ
  * Because of this, `nni(αu,u,uv,v,vδ, ...)` should not be used directly; use instead `nni!(uv, move_number)`.
  * nni!(undoinfo...) restores the topology, but edges below hybrid nodes will have length 0.0 even if they didn't before.

Node numbers and edge numbers are not modified. Edge `uv` keeps its direction unchanged *unless* the directions were `α -> u -> v -> δ` or `α <- u <- v <- δ`, in which case the direction of `uv` is flipped.

The second version's input has the same signature as the output, but will undo the NNI more easily. This means that if `output = nni!(input)`, then `nni!(output...)` is valid and undoes the first operation.

Right now, branch lengths are not modified except when below a hybrid node. Future versions might implement options to modify branch lengths.
