```
aws_mqtt5_negotiated_settings_copy(source, dest)
```

交渉された設定構造の所有コピーを作成します。

下流で使用されます。

# 引数

  * `source`: コピー元の設定
  * `dest`: コピー先の設定。コピープロセスの最初のステップとしてクリーンアップが呼び出されるため、ゼロ初期化または初期化された状態でなければなりません。

# 戻り値

成功/失敗

### プロトタイプ

```c
int aws_mqtt5_negotiated_settings_copy( const struct aws_mqtt5_negotiated_settings *source, struct aws_mqtt5_negotiated_settings *dest);
```
