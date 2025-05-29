```
Observable(t, name; keyargs...)
```

タイプ`t`のオブザーバブルを作成します。

次のキーワードが許可されています：

  * `alloc`: 時系列コンテナの事前割り当てサイズ
  * `outfile`: 入出力操作のためのデフォルトHDF5/JLD出力ファイル
  * `group`: `outfile`内のターゲットパス
  * `inmemory`: 時系列をメモリ内またはディスク上に保持するかどうか
  * `meantype`: 平均のタイプ（測定タイプ`t`と互換性があるべき）

詳細は[`Observable`](@ref)を参照してください。
