```
ERA5Variable
```

ERA5変数の抽象スーパタイプで、以下のサブタイプがあります。

```
SingleLevel   <: ERA5Variable
PressureLevel <: ERA5Variable
```

すべての `ERA5Variable` タイプは以下のフィールドを含みます：

  * `ID` : 変数のIDで、NetCDFファイル内の識別子でもあります
  * `name` : 変数のフルネーム
  * `long` : 変数のロングネームで、CDSからの取得を指定するために使用されます
  * `dataset` : 変数のフルネーム
  * `units` : 変数の単位

すべての `PressureLevel` タイプは以下のフィールドを含みます：

  * `hPa` : 興味のある圧力変数の圧力レベル（hPa単位）
