```
petab_select(path_yaml, alg; nmultistarts = 100, kwargs...) -> path_res
```

PEtab-select問題に対して、PEtab選択問題ファイルに指定された方法でモデル選択を実行します。モデル選択結果を含むYAMLファイルへのパス（`path_res`）を返します。

一般的なモデル選択（例えば、フォワードサーチを使用する場合）のオプションは、PEtab-selectファイルに指定されています。これを設定する方法の詳細については、PEtab-selectの[ドキュメント](https://github.com/PEtab-dev/petab_select)を参照してください。

モデル選択の各ラウンドでは、候補モデルがマルチスタートパラメータ推定を使用してパラメータ推定され、各モデルに対して`nmultistarts`が実行されます。パラメータ推定から得られた目的値は、次のラウンドのモデル評価に使用されます。

利用可能で推奨される最適化アルゴリズムのリスト（`alg`）は、パッケージのドキュメントおよび[`calibrate`](@ref)のドキュメントに記載されています。

さらに[`calibrate_multistart`](@ref)も参照してください。

## キーワード引数

  * `kwargs`: [`PEtabODEProblem`](@ref)および[`calibrate`](@ref)で受け入れられる同じキーワード。
