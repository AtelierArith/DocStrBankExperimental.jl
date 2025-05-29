Stanのcmdstan実行可能ファイルによって作成された.csv出力ファイルを読み込み、（ネストされた）変数を抽出します。

```julia
extract_reshape(a3d, col_names, var; nested)

```

### 必要な引数

```julia
* `a3d` : Array n_samples x n_variables x n_chains
* `col_names` : 名前のベクトル
* `var` : 要求された（ネストされた）列
```

### キーワード引数

```julia
* `nested` : trueの場合、nsamples x nchainsの行列を返します。そうでない場合は単一の行列を返します。
```

エクスポートされました
