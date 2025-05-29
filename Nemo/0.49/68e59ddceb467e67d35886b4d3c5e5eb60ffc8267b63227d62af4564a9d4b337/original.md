```
teichmuller(a::QadicFieldElem)
```

Return the Teichmuller lift of the $q$-adic value $a$. We require the valuation of $a$ to be non-negative. The precision of the output will be the same as the precision of the input. For convenience, if $a$ is congruent to zero modulo $q$ we return zero. If the input is not valid an exception is thrown.
