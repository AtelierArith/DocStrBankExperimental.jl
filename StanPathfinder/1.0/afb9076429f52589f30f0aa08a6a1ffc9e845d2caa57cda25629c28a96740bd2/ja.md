# PathfinderModel

PathfinderModelを作成し、Stan言語モデルをコンパイルします。

```julia
PathfinderModel(name, model)
PathfinderModel(name, model, tmpdir)

```

### 必須引数

```julia
* `name::AbstractString`        : モデルの名前
* `model::AbstractString`       : Stanモデルソース
```

### オプションの位置引数

```julia
* `tmpdir::AbstractString`      : 出力ファイルが保存されるディレクトリ
```

エクスポート済み。
