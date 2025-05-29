```
companion_matrix(p::PolyRingElem) -> MatElem
```

$$
p = \sum_{i=0}^n a_ix^i
$$

の伴随行列を返します。すなわち、行列は次のようになります。

```
0 1  0  $\dots$  0
0  0  1  $\dots$  0
$\vdots$  $\vdots$  $\ddots$  $\vdots$  $\vdots$
0  0  $\vdots$  0  1
$-a_0$  $-a_1$  $-a_2$  $\dots$  $-a_{n-1}$
```
