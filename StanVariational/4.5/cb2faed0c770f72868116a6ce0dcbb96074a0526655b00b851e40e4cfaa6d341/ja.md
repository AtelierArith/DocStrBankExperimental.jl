# VariationalModel

VariationalModelを作成し、Stan言語モデルをコンパイルします。

### 必要な引数

```julia
* `name::AbstractString`        : モデルの名前
* `model::AbstractString`       : Stanモデルソース
```

### オプションの位置引数

```julia
 `tmpdir::AbstractString`             : 出力ファイルが保存されるディレクトリ
```
