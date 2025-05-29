SampleModelを作成し、Stan言語モデルをコンパイルします。

```julia
SampleModel(name, model)
SampleModel(name, model, tmpdir)

```

# 拡張ヘルプ

### 必須引数

```julia
* `name::AbstractString`               # モデルの名前
* `model::AbstractString`              # Stanモデルソース
```

### オプションの位置引数

```julia
* `tmpdir`                             # 出力ファイルが保存されるディレクトリ
                                       # デフォルト: `mktempdir()`
```

注意: Windowsでは`tmpdir`を使用する際に問題が発生することがあります。
