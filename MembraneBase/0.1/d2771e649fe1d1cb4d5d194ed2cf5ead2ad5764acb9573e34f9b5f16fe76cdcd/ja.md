```
IsothermData(; 
    partial_pressures_mpa=nothing, concentrations_cc=nothing, activities=nothing, temperature_k=nothing, 
    rho_pol_g_cm3=nothing, pen_mws_g_mol=nothing,
)
```

等温線に関連するすべてのデータのコンテナ。

各成分およびステップに特有のデータは、列が成分を表し、行がステップを表す行列形式で整理されています。すなわち、s -> ステップおよび c -> 成分：

```
    [ s1c1  s1c2  s1c3 ...
      s2c1  s2c2  s2c3 ...
      s3c1  s3c2  s3c3 ...
      ...   ...   ...  ... ]
```

# 入力

入力はベクトルのベクトルであることができます。例えば、`partial_pressures_mpa = [[component_1-step_1, component_1-step_2, ...], [component_2-step_1, component_2-step_2, ...], ...]` または、成分が1つだけの場合は、単にベクトル `[step_1, step_2, ...]` だけでも構いません。
