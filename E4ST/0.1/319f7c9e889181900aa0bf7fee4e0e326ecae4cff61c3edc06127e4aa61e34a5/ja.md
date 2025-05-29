```
E4ST.modify_setup_data!(pol::ITCStorage, config, data)
```

各シミュレーション年の適格発電機に対して、ITCStorage値を持つgenテーブルに列を作成します。

ITCStorage値は`capex_obj`に基づいて計算されるため、ITCStorage値は発電機の`year_on`でのみ適用されます。
