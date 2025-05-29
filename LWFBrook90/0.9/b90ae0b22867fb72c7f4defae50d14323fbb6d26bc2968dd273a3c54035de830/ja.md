```
get_water_partitioning(simulation)
```

異なるフラックスを列として、時間ステップを行として持つ水フラックスの3つの2D DataFrameを返します。3つのDataFrameは、日次、月次、年次の解像度であり、シミュレーション全体をカバーしています。

例     df*part*daily, df*part*monthly, df*part*yearly = get*water*partitioning(simulation)
