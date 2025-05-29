```
PEtabMultistartResult
```

`calibrate_multistart`を用いたマルチスタート最適化からのパラメータ推定統計。

[`calibrate_multistart`](@ref)および[`PEtabOptimisationResult`](@ref)も参照してください。

## フィールド

  * `xmin`: すべての実行の中での最良の最小化者。
  * `fmin`: すべての実行の中での最良の最小値。
  * `alg`: パラメータ推定アルゴリズム。
  * `nmultistarts`: パラメータ推定の実行回数。
  * `sampling_method`: 開始点を生成するために使用されるサンプリング方法。
  * `dirsave`: `calibrate_multistart`に`dirsave`が提供された場合にパラメータ推定実行統計が保存されるディレクトリのパス。
  * `runs`: 各実行のパラメータ推定結果を持つ`PEtabOptimisationResult`のベクター。

```
PEtabMultistartResult(dirres::String; which_run::String="1")
```

`dirres`に保存されたマルチスタートパラメータ推定結果をインポートします。

新しい最適化実行が行われるたびに、結果は一意の数値の末尾で保存されます。特定の実行からの結果は、`which_run`で数値の末尾を指定することで取得できます。
