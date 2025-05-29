```
primitivize(op::SymOperation, cntr::Char, modw::Bool=true) --> typeof(op)
```

Return a symmetry operation `op′` $≡ \{W'|w'\}$ in a primitive setting, transformed from an input symmetry operation `op` $= \{W|w\}$ in a conventional setting. The operations $\{W'|w'\}$ and $\{W|w\}$ are related by a transformation $\{P|p\}$ via (cf. Section 1.5.2.3 of [^ITA6]):

$$
\{W'|w'\} = \{P|p\}⁻¹\{W|w\}\{P|p\}.
$$

where $P$ and $p$ are the basis change matrix and origin shifts, respectively. The relevant transformation $\{P|p\}$ is inferred from the centering type, as provided by `cntr` (see also [`Bravais.centering`](@ref)).

By default, translation parts of `op′`, i.e. $w'$ are reduced modulo 1 (`modw = true`); to disable this, set `modw = false`.

[^ITA6]: M.I. Aroyo, International Tables of Crystallography, Vol. A, 6th ed. (2016).
