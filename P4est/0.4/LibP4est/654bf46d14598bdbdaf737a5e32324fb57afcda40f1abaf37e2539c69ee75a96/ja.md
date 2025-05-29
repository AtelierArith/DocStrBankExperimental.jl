```
p6est_copy(input, copy_data)
```

`p6est`のディープコピーを作成します。接続は複製されません。四分木のユーザーデータのコピーはオプションです。古いデータと新しいデータのサイズが0の場合、user_dataフィールドは必ずコピーされます。

### パラメータ

  * `copy_data`:[in] trueの場合、データがコピーされます。falseの場合、data_sizeは0に設定されます。

### 戻り値

入力に依存しない有効な`p6est`を返します。

### プロトタイプ

```c
p6est_t *p6est_copy (p6est_t * input, int copy_data);
```
