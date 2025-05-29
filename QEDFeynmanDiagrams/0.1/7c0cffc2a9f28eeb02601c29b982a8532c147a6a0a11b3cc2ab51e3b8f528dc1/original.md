```
number_of_diagrams(proc::AbstractProcessDefinition)
```

For a given [`QEDbase.AbstractProcessDefinition`](@extref), returns the number of valid Feynman diagrams at tree-level. This is equivalent to

$$
\frac{(M + 3N - 3)!}{(2N - 1)!} * E! * U! * T!
$$


, where
$M \dots$ number of external photons,
$E \dots$ number of electron lines,
$U \dots$ number of muon lines,
$T \dots$ number of tauon lines, and
$N = E + U + T$.
 An electron/muon/tauon "line" is a pair of incoming fermion and outgoing anti-fermion or vice versa.
