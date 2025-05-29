```
Path(file, type = :YAML)
```

Pathは計算コンテキストのためのデータ構造です。関数Path()は、列車の実行パスを作成します。サポートされているフォーマットは次のとおりです: railtoolkit/schema (2022.05)

# 例

```
julia> my_path = Path("file.yaml") # YAMLファイルからパスを生成します。
Path(variables)
```
