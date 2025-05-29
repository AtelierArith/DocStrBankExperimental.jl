```
read_from_gfa(filename::String; weight_file::String)
```

GFAファイルからグラフを読み込み、オプションのweight_file（`node`と`weight`の2列を含む）を指定し、`GFAResult`構造体を返します。この構造体には、`g` - グラフ、`w` - 重み配列、`l` - ノードラベル配列、`e` - エッジラベル配列、`p` - パス配列が含まれています。
