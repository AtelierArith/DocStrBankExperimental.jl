```
read_YAML(filename::String)
```

[YAML](https://yaml.org/) 形式で保存されたニューラルネットワークを読み込みます。この関数は [`YAML.jl` ライブラリ](https://github.com/JuliaData/YAML.jl) をロードする必要があります。

### 入力

  * `filename` – `YAML` ファイルの名前

### 出力

[`FeedforwardNetwork`](@ref)。
