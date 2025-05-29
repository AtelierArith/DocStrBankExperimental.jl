```
@debounce フィールド名 ms

@debounce アプリ フィールド名 ms
```

フィールド固有のデバウンスタイムをmsで設定します。

### パラメータ

  * `APP`: ReactiveModelのサブタイプ、例: `MyApp`
  * `フィールド名`: 宣言に書かれたフィールド名またはフィールド名、例: `x`, `(x, y, z)`
  * `ms`: msでのデバウンスタイム

### 例

#### 暗黙のアプリ

```
@app begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# 高速メッセージングのためのデバウンスなし
@debounce quick 0

# 長時間実行されるタスクのための長いデバウンス
@debounce (slow1, slow2) 1000
```

#### 明示的なアプリ

```
@app MyApp begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# 高速メッセージングのためのデバウンスなし
@debounce MyApp quick 0

# 長時間実行されるタスクのための長いデバウンス
@debounce MyApp slow 1000
```
