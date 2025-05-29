```
manipulate(f::Function; parameters, config=())
```

コールバック `f` によって更新されるインタラクティブなプロットを作成します。Jupyter Notebook でのみ動作します。

# 引数

  * `f::Function`: プロットを生成するためのコールバック; インタラクティブに更新される設定 `c` が提供されます。
  * `parameters`: インタラクティブウィジェットで調整可能なパラメータ; 値は反復可能である必要があります。
  * `config=()`: ベースライン設定。
