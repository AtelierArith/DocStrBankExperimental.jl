# OptimizeModel

OptimizeModelを作成し、Stan言語モデルをコンパイルします。

### 必要な引数

```julia
* `name::AbstractString`        : モデルの名前
* `model::AbstractString`       : Stanモデルソース
```

### オプションの引数

```julia
* `tmpdir=mktempdir()`          : 出力ファイルが保存されるディレクトリ
```
