```
QFIM_obj(;W=nothing, eps=GLOBAL_EPS, LDtype::Symbol=:SLD)
```

Choose QFI [$\mathrm{Tr}(WF^{-1})$] as the objective function with $W$ the weight matrix and $F$ the QFIM.

  * `W`: Weight matrix.
  * `eps`: Machine epsilon.
  * `LDtype`: Types of QFI (QFIM) can be set as the objective function. Options are `:SLD` (default), `:RLD` and `:LLD`.
