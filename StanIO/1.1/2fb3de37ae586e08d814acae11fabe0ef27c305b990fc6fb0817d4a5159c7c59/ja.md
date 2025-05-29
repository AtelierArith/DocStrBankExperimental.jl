Stanのcmdstan実行可能ファイルによって作成された.csv出力ファイルを読み取ります。

```julia
read_csvfiles(
    csvfiles,
    output_format;
    include_internals,
    return_parameters,
    n_chains,
    n_samples,
    kwargs...
)

```

# 拡張ヘルプ

### 必須引数

```julia
* `csvfiles` : ファイル名のベクター
* `output_format` : 要求された出力形式
```

### オプション引数

```julia
* `include_internals=true` : output_formatに内部パラメータを含める
* `return_parameters=false` : .csvファイルのようにパラメータ名を返す
* `n_chains=length(csvfiles)` : チェーンの数
* `n_samples=1000`: サンプルの数
* `kwargs...`
```

エクスポートされていません
