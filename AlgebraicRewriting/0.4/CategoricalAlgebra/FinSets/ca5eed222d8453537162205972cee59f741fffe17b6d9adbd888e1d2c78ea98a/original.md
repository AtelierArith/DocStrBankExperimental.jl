Compute a pushout complement of finite sets, if possible.

Given functions $l: I → L$ and $m: L → G$ to form a pushout square

```
l
```

L ← I m ↓   ↓k   G ← K     g

define the set $K := G / m(L / l(I))$ and take $g: K ↪ G$ to be the inclusion. Then the map $k: I → K$ is determined by the map $l⋅m: I → G$ from the requirement that the square commutes.

Pushout complements exist only if the identification condition is satisfied. An error will be raised if the pushout complement cannot be constructed. To check this in advance, use [`can_pushout_complement`](@ref).
