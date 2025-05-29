```
iftrue(bool_condition, value)
iftrue(func, bool_condition)
iftrue(bool_condition) do
  # bool_conditionがtrueの場合のみ実行される
end
```

条件に基づいてOptionを作成するためのヘルパー。`bool_condition`がtrueの場合、関数`func`が引数なしで呼び出され、その結果が`Identity`にラップされます。`bool_condition`がfalseの場合、`Option()`が返されます。
