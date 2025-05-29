```
aws_secure_tunnel_message_type_to_c_string(message_type)
```

メッセージタイプの const char 説明を取得します

# 引数

  * `message_type`: セキュアトンネルメッセージで使用されるメッセージタイプ

# 戻り値

メッセージタイプの const char 翻訳

### プロトタイプ

```c
const char *aws_secure_tunnel_message_type_to_c_string(enum aws_secure_tunnel_message_type message_type);
```
