```
StockAndFlowF(s,p,v,f,sv)
```

例: 動的変数を定義する際は、正しい順序で定義する必要があります。

```julia
sir_StockAndFlow=StockAndFlowF((:S=>(:F_NONE,:inf,:N), :I=>(:inf,:F_NONE,:N)),
 (:c, :beta),
 (:v_prevalence=>(:I,:N,:/),:v_meanInfectiousContactsPerS=>(:c,:v_prevalence,:*),:v_perSIncidenceRate=>(:beta,:v_meanInfectiousContactsPerS,:*),:v_newInfetions=>(:S,:v_perSIncidenceRate,:*)),
 (:inf=>:v_newInfetions),
 (:N))
```
