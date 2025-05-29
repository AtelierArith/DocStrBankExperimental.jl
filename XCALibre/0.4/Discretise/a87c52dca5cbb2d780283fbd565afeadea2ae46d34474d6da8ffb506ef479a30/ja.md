```
FixedTemperature <: AbstractDirichlet
```

固定温度境界条件モデルで、ユーザーがエネルギー特定モデルに変換可能な壁温度を指定できるようにします。例えば、感熱エンタルピーなどです。

### フィールド

  * 'ID' – 境界ID
  * `value` – ディリクレ境界条件のスカラーまたはベクトル値。
  * `T` - ケルビンでの温度値。
  * `model` - ケースのエネルギー物理モデル。

### 例

```
FixedTemperature(:inlet, T=300.0, model=model.energy),
```
