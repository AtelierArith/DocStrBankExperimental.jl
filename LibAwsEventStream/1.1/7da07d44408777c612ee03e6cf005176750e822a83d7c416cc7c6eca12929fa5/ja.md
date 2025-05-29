```
aws_event_stream_headers_list_cleanup(headers)
```

ヘッダーリストをクリーンアップします。また、文字列やバッファのコピーフラグの結果であったヘッダーも解放します。

### プロトタイプ

```c
void aws_event_stream_headers_list_cleanup(struct aws_array_list *headers);
```
