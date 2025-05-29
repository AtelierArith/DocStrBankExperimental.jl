```
fmi3FreeInstance!(c::FMU3Instance; popInstance::Bool = true)
```

指定されたインスタンスを破棄し、読み込まれたモデルをアンロードし、FMUインターフェースの関数によって割り当てられたすべてのメモリおよびその他のリソースを解放します。「c」にnullポインタが提供された場合、関数呼び出しは無視されます（効果はありません）。

コンポーネントをFMUのコンポーネントリストから削除します。

# 引数

  * `c::FMU3Instance`: 引数 `c` は、FMI 3.0標準におけるFMUのインスタンス化されたインスタンスを表すミュータブル構造体です。

# キーワード

  * `popInstance::Bool=true`: キーワード `popInstance = true` の場合、解放されたインスタンスは削除されます。

# 戻り値

  * 何も返さない

# ソース

  * FMISpec3.0 リンク: [https://fmi-standard.org/](https://fmi-standard.org/)
  * FMISpec3.0, バージョン D5ef1c1: 2.3.1. スーパー状態: FMU状態設定可能
