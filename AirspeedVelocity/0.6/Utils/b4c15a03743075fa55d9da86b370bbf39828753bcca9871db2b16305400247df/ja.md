```
load_results(specs::Vector{PackageSpec}; input_dir::String=".")
```

`specs`ベクター内の各PackageSpecに対してJSONファイルから結果を読み込みます。この関数は、JSONファイルが`input_dir`ディレクトリにあり、"results_{s}.json"という名前であると仮定します。ここで`s`は`PackageName@Rev`に等しいです。

この関数は、`combined_plots`関数に入力するための結合されたOrderedDictを返します。

# 引数

  * `specs::Vector{PackageSpec}`: 読み込む各パッケージのリビジョンのベクター（`PackageSpec`として）。
  * `input_dir::String="."`: 結果があるディレクトリ。デフォルトは現在のディレクトリです。

# 戻り値

  * `OrderedDict{String,OrderedDict}`: `combined_plots`関数に渡す準備が整った結合結果。
