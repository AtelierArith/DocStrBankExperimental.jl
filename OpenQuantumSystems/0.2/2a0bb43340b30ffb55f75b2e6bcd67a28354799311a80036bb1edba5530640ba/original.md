```
get_rho_bath(rho, agg, FCProd, aggIndices, vibindices; justCopy=false)
```

This method will return the bath part of `rho` knowing the result of [`trace_bath`](@ref) defined as follows

$\rho_\text{bath} = \operatorname{tr}_S \{\rho\}$

$\rho_{\text{bath}, ab} = \rho_{ab} / \langle a \vert \operatorname{tr}_B \{ \rho \}\vert b \rangle$
