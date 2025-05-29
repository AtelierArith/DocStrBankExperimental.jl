```
aws_http_library_clean_up()
```

aws-c-httpで使用される内部データ構造をクリーンアップします。aws-c-httpの機能を使用しているアプリケーションが終了するまで呼び出してはいけません。

### プロトタイプ

```c
void aws_http_library_clean_up(void);
```
