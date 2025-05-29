function need*to*interrupt(OutputDir::String)

```
フォルダ `OutputDir` に `stop` という名前のファイルがある場合は true を返し、そうでなければ `false` を返します。
```

## キーワード

  * `remove`: true の場合、`stop` ファイルを非同期で削除します
  * `delay`: true の場合、ファイルロックエラーを避けるために 0.1 秒待ちます
