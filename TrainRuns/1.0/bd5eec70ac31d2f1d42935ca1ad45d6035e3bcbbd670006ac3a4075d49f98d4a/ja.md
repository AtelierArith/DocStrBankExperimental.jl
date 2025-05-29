```
Train(file, type = :YAML)
```

Trainは計算コンテキストのためのデータ構造です。関数Train()は計算に使用するための列車を作成します。YAMLファイルのサポートされているフォーマットは：railtoolkit/schema (2022.05)

# 例

```
julia> my_train = Train("file.yaml") # YAMLファイルから列車を生成します。
Train(variables)
```
