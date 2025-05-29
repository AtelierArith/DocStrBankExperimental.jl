```
StockAndFlowF(s,p,v,f,sv)
```

EXAMPLE: when define the dynamical variables, need to define with the correct order

```julia
sir_StockAndFlow=StockAndFlowF((:S=>(:F_NONE,:inf,:N), :I=>(:inf,:F_NONE,:N)),
 (:c, :beta),
 (:v_prevalence=>(:I,:N,:/),:v_meanInfectiousContactsPerS=>(:c,:v_prevalence,:*),:v_perSIncidenceRate=>(:beta,:v_meanInfectiousContactsPerS,:*),:v_newInfetions=>(:S,:v_perSIncidenceRate,:*)),
 (:inf=>:v_newInfetions),
 (:N))
```
