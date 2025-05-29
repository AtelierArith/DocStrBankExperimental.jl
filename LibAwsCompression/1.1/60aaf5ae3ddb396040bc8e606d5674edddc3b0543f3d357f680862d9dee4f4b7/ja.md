```
aws_compression_library_clean_up()
```

aws-c-compressionで使用される内部データ構造をクリーンアップします。aws-c-compressionの機能を使用しているアプリケーションが完了するまで呼び出してはいけません。

### プロトタイプ

```c
void aws_compression_library_clean_up(void);
```
