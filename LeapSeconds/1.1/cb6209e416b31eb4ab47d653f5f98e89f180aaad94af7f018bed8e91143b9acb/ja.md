```
offset_utc_tai(dt::DateTime)
```

与 Coordinated Universal Time (UTC) と International Atomic Time (TAI) の違いを、UTC の指定された `DateTime` に対して返します。

$$
\Delta AT = UTC - TAI
$$

!!! warning
    Julia の標準ライブラリの `DateTime` 型は、うるう秒の間の UTC 日付を表現できません。例えば、「2016-12-31T23:59:60.0」は有効な `DateTime` として解析されず、エラーが発生します。[AstroTime.jl](https://github.com/JuliaAstro/AstroTime.jl) パッケージは、うるう秒に対応した `Epoch` 型を提供しており、代替として使用できます。

