```
get_rho_bath(rho, agg, FCProd, aggIndices, vibindices; justCopy=false)
```

このメソッドは、次のように定義された[`trace_bath`](@ref)の結果を知っている場合に`rho`のバス部分を返します。

$$
\rho_\text{bath} = \operatorname{tr}_S \{\rho\}
$$

$$
\rho_{\text{bath}, ab} = \rho_{ab} / \langle a \vert \operatorname{tr}_B \{ \rho \}\vert b \rangle
$$
