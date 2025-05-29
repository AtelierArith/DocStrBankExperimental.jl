```
p4est_copy_ext(input, copy_data, duplicate_mpicomm)
```

`p4est`のディープコピーを作成します。接続は複製されません。四分木のユーザーデータのコピーはオプションです。古いデータと新しいデータのサイズが0の場合、user_dataフィールドは常にコピーされます。コピーのinspectメンバーはNULLに設定されます。コピーのリビジョンカウンターはゼロに設定されます。

### パラメータ

  * `copy_data`:[in] trueの場合、データがコピーされます。falseの場合、data_sizeは0に設定されます。
  * `duplicate_mpicomm`:[in] trueの場合、MPIコミュニケーターがコピーされます。

### 戻り値

入力に依存せず、同じ接続を借用する有効な`p4est`を返します。そのリビジョンカウンターは0です。

### プロトタイプ

```c
p4est_t *p4est_copy_ext (p4est_t * input, int copy_data, int duplicate_mpicomm);
```
