```
lsrtm_objective(model, source, dobs, dm; options=Options(), nlind=false)
```

最小二乗移動目的関数を評価します。関数値と勾配のタプルを返します。`model`は現在の速度モデルを持つ`Model`構造体であり、`source`と`dobs`は`judiVector`型の波形と観測データです。

# 例

```
function_value, gradient = lsrtm_objective(model, source, dobs, dm)
```
