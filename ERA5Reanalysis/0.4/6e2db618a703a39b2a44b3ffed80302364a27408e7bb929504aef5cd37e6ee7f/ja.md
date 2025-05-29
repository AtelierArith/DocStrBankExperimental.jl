```
PressureLevel <: ERA5Variable
```

単一レベル変数のための抽象スーパタイプで、以下のサブタイプがあります：

```
PressureVariable <: PressureLevel
PressureCustom   <: PressureLevel
```
