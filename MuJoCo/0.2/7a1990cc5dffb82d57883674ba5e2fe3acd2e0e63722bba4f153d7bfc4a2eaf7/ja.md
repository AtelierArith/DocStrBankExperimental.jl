```
load_model(path)
```

拡張子によってファイルの種類を判別し、モデルをメモリにロードします。

このモデルをシミュレーターで使用するには、[`init_data`](@ref)を使用して取得した対応するデータも必要です。

期待されるファイルタイプ: 'xml', 'mjcf', または 'mjb'（または大文字のバリエーション）。

# 例

```julia
model = load_model(MuJoCo.humanoid_model_file())
data = init_data(model)
```
