```
assert_comment(condition, message)
```

指定された `condition` が真であることを確認します。`condition` が偽の場合、関数は提供された `message` とともに AssertionError をスローします。

# 引数

  * `condition`: チェックされる条件。
  * `message`: アサーションが失敗した場合に表示されるメッセージ。

# 例

```julia
assert_comment(1 == 1, "Numbers are not equal") # エラーはスローされません
assert_comment(1 == 2, "Numbers are not equal") # AssertionError がスローされます
```
