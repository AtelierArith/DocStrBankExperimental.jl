```
adjust_rake(localaniso, azimuths)
adjust_rake!(localaniso, azimuths)
```

主方向 :X を指定された方位に沿って調整します。これにより :X と :Y の方向が変更され、:Z は変更されません。これは、楕円体が正しい :Z を持っている場合（例：体の厚さに沿って）に便利ですが、主方向は主平面上の特定の方位に合わせる必要があります。

## 例

`localaniso` 変数に三つの楕円体を考慮します。

```julia
azimuths = [25.0, 30.0, 40.0]
newpars = adjust_rake(localaniso, azimuths)
```
