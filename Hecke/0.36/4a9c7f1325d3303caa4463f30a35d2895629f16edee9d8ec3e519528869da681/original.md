```
is_local_norm(mkK::Map, a::AbsSimpleNumFieldElem) -> Bool
```

Let         `mkK : k \to K` be a map (embedding) of number fields.    

Tests if $a$ is a local norm for the relative extension implicit in the map. That is for a prime ideal $p$ in $k$ let $Q_i$ the primes above. $a$ is a local norm if there are $b_i$ in the completions at $Q_i$ s.th. the      `\prod N(b_i) = q` where the norm $N$ is form the completion at $Q_i$ down to the completion at $p$.  
