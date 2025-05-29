```
TokenCounts(; input=0, output=0, cache_write=0, cache_read=0)
```

異なるカテゴリにわたるトークンの使用状況を追跡します：

  * `input`: プロンプト内の新しいトークンの数（キャッシュされたトークンを除く）
  * `output`: 応答で生成されたトークンの数
  * `cache_write`: キャッシュに書き込まれたトークンの数
  * `cache_read`: キャッシュから読み取られたトークンの数

注意：総入力トークン = input + cache*write + cache*read
