```
SSD_examples::Dict{Symbol,String}
```

パッケージによって提供される例の検出器設定ファイルへのパスを持つ辞書です。

辞書の可能なキーを `keys(SSD_examples)` で見つけることができます。

例の検出器設定ファイルは次のようにロードできます。

```
path_to_config_file = SSD_examples[:InvertedCoax]
sim = Simulation(path_to_config_file)
```
