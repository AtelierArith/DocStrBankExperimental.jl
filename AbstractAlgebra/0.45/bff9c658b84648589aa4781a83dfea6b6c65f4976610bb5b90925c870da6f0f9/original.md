```
residue_field(R::Ring, a::RingElement; cached::Bool = true)
```

Create the residue ring $R/(a)$ where $a$ is an element of the ring $R$. We require $a \neq 0$. If `cached == true` (the default) then the resulting residue ring parent object is cached and returned for any subsequent calls to the constructor with the same base ring $R$ and element $a$.
