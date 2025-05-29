```
@throttle フィールド名 ms

@throttle アプリ フィールド名 ms
```

フィールド固有のスロットル時間をmsで設定します。

### パラメータ

  * `APP`: ReactiveModelのサブタイプ、例: `MyApp`
  * `フィールド名`: 宣言に記載されたフィールド名またはフィールド名、例: `x`, `(x, y, z)`
  * `ms`: msでのスロットル時間

### 例

#### 暗黙のアプリ

```
@app begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# 高速メッセージングのためのスロットリングなし
@throttle quick 0

# 長時間実行されるタスクのための長いスロットリング
@throttle (slow1, slow2) 1000
```

#### 明示的なアプリ

```
@app MyApp begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# 高速メッセージングのためのスロットリングなし
@throttle MyApp quick 0

# 長時間実行されるタスクのための長いスロットリング
@throttle MyApp slow 1000
```
