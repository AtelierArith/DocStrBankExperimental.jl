```
p6est_copy_ext(input, copy_data, duplicate_mpicomm)
```

`p6est`のディープコピーを作成します。接続は複製されません。四分木のユーザーデータのコピーはオプションです。古いデータと新しいデータのサイズが0の場合、user_dataフィールドは常にコピーされます。コピーのinspectメンバーはNULLに設定されます。

### パラメータ

  * `copy_data`:[in] trueの場合、データがコピーされます。falseの場合、data_sizeは0に設定されます。
  * `duplicate_mpicomm`:[in] trueの場合、MPIコミュニケーターがコピーされます。

### 戻り値

入力に依存しない有効な`p6est`を返します。

### プロトタイプ

```c
p6est_t *p6est_copy_ext (p6est_t * input, int copy_data, int duplicate_mpicomm);
```
