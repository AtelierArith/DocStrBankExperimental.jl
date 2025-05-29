```
BBHostPlatform()
```

これは、juliaのバージョン、libgfortranのバージョンなどに関する制約を含まない、`HostPlatform()`の簡略化された形式を提供します。これは、ホストマシンで動作する最も一般的な形式が必要であり、Juliaのすべての依存関係との互換性を気にしない場合に便利です。このプラットフォームには、arch、os、libcタイプ、およびcxxstring_abiが含まれます。
