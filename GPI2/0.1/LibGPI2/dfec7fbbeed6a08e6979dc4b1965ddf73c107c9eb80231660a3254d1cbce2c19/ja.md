```
gaspi_initialized(initialized)
```

GPI-2が初期化されているか確認します

### パラメータ

  * `initialized`: フラグ値を持つ出力パラメータ。

### 戻り値

成功した場合はGASPI*SUCCESS、エラーの場合はGASPI*ERRORを返します。

### プロトタイプ

```c
gaspi_return_t gaspi_initialized (gaspi_number_t * initialized);
```
