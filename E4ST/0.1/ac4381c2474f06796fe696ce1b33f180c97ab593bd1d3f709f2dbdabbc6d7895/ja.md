```
modify_setup_data!(mod::FuelPrice, config, data)
```

`gen` テーブルの `fuel_price` 列をゼロに設定します。これは、この修正によって後で上書きされるため、燃料コストの二重計上を避けるためです。
