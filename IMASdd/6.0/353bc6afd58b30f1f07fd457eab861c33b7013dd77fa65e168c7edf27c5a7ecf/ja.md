```
hdf2imas(filename::AbstractString, target_path::AbstractString; error_on_missing_coordinates::Bool=true, verbose::Bool=false, kw...)
```

HDF5ファイルからオブジェクトを簡単なエントリーポイントを使用してロードします。ファイルと内部ターゲットパス（文字列として）を指定すると、関数はデータセットの値またはグループから構築されたIMAS ids構造体のいずれかを返します。

`target_path`にあるオブジェクトがグループであり、"concrete*type"属性を持っている場合、そのタイプが評価されてインスタンス化されます。そうでない場合は、デフォルト（`dd()`）が使用されます。座標データは`error*on*missing*coordinates`に基づいて処理されます。

# 引数

  * `filename`: HDF5ファイルへのパス
  * `target_path`: 希望するデータセットまたはグループへの内部HDF5パス
  * `error_on_missing_coordinates`（デフォルト: `true`）: 座標チェックを強制
  * `verbose`（デフォルト: `false`）: 詳細ログを有効にする
  * `kw...`: `HDF5.h5open`に渡される追加のキーワード引数

# 戻り値

データセットの値または構築されたIMAS ids。
