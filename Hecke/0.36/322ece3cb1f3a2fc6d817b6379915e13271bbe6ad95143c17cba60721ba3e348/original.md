```
companion_matrix(p::PolyRingElem) -> MatElem
```

Returns the companion matrix of $p = \sum_{i=0}^n a_ix^i$, i.e. the matrix

```
0 1  0  $\dots$  0
0  0  1  $\dots$  0
$\vdots$  $\vdots$  $\ddots$  $\vdots$  $\vdots$
0  0  $\vdots$  0  1
$-a_0$  $-a_1$  $-a_2$  $\dots$  $-a_{n-1}$
```
