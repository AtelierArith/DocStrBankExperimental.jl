```
aws_mqtt_validate_utf8_text(text)
```

MQTT仕様に基づいてutf-8文字列を検証します

# 引数

  * `text`:

# 戻り値

テキストが検証されていればAWS*OP*SUCCESS、そうでなければAWS*OP*ERR

### プロトタイプ

```c
int aws_mqtt_validate_utf8_text(struct aws_byte_cursor text);
```
