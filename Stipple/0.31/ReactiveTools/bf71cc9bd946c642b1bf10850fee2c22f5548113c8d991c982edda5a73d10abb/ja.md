```
@clear_throttle

@clear_throttle fieldname

@clear_throttle App

@clear_throttle App fieldname
```

フィールド固有のスロットル時間をクリアします。設定については `@throttle` を参照してください。`@clear throttle` を呼び出すと、フィールドは `@init` マクロで指定された値によってスロットルされます。

### 例

#### 暗黙のアプリ

```
@app begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end


# すべてのフィールドの標準スロットル時間を設定
@page("/", ui, model = MyApp, throttle = 100)

# 高速メッセージングのためのスロットルなし
@throttle quick 0
@throttle slow 1000

# アプリの標準値にリセット
@clear_throttle quick

# すべてのフィールド固有のスロットル時間をクリア
@clear_throttle
```

#### 明示的なアプリ

```
@app MyApp begin
  @out quick = 12
  @out slow = 12
  @in s = "Hello"
end

# すべてのフィールドの標準スロットル時間を設定
@page("/", ui, model = MyApp, throttle = 100)

# 高速メッセージングのためのスロットルなし
@throttle MyApp quick 0

@clear_throttle MyApp quick

# すべてのフィールド固有のスロットル時間をクリア
@clear_throttle MyApp
```
