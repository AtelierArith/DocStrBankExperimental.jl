```
extract_evotrees_info(evo_model; tree_limit=length(evo_model.trees))
```

[EvoTrees](https://github.com/Evovest/EvoTrees.jl) モデル `evo_model` から対応する MIP を構築するために必要なデータを取得します。必要な情報を含むカスタムデータ型 `TEModel` を返します。

# 引数

  * `evo_model`: 訓練された EvoTrees ツリーアンサンブルモデル。

# オプション引数

  * `tree_limit`: 引数で指定された最初の *n* 本のツリーのみが使用されます。
