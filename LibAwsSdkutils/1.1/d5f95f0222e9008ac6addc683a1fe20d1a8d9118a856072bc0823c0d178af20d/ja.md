```
aws_get_credentials_file_path(allocator, override_path)
```

プロファイル認証情報ファイルの最終的なプラットフォーム固有のパスを計算します。制限されたホームディレクトリの展開/解決を行います。

override_pathがnullでない場合、標準のホームディレクトリ設定パスを使用する代わりに最初に検索されます。

### プロトタイプ

```c
struct aws_string *aws_get_credentials_file_path( struct aws_allocator *allocator, const struct aws_byte_cursor *override_path);
```
