```
load_json(file::String = "spectral-indices-dict.json")
```

`data` フォルダから指定された JSON ファイルを読み込みます。

# 引数

  * `file::String = "spectral-indices-dict.json"`: 読み込む JSON ファイルの名前。

# 戻り値

  * `object`: 指定されたファイルから解析された JSON コンテンツ。

# 例

```julia
# デフォルトの JSON ファイルを読み込む
data = load_json()

# 特定の JSON ファイルを読み込む
data = load_json("my-custom-indices.json")
```
