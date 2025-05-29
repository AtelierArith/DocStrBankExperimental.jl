```
crit_mix(model::EoSModel,z;v0=x=x0_crit_mix(model,z))
```

与えられた組成における臨界混合点を返します。

次の要素を含むタプルを返します：

  * 臨界混合温度 `[K]`
  * 臨界混合圧力 `[Pa]`
  * 臨界混合体積 `[m³]`
