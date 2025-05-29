```
init_variables(models...)
```

モデル変数をデフォルト値で初期化しました。変数はモデルの入力と出力から取得されます。

# 例

```@example
using PlantSimEngine

# パッケージに例として示されているダミーモデルをロードします：
using PlantSimEngine.Examples

init_variables(Process1Model(2.0))
init_variables(process1=Process1Model(2.0), process2=Process2Model())
```
