Stanのcmdstan実行可能ファイルによって作成された.csv出力ファイルを読み込み、（可能性のある）ネストされた変数を抽出します。

```julia
extract_reshape(csvfiles, var; nested)

```

### 必須引数

```julia
* `csvfiles` : ファイル名のベクター
* `var` : 要求された（ネストされた）列
```

### キーワード引数

```julia
* `nested` : trueの場合、nsamples x nchainsの行列を返し、そうでない場合は単一の行列を返します
```

エクスポートされました
