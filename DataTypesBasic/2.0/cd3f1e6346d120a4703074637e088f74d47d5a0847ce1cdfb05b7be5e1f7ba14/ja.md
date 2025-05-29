```
iffalse(bool_condition, value)
iffalse(func, bool_condition)
iffalse(bool_condition) do
  # bool_conditionがtrueの場合のみ実行されます
end
```

条件に基づいてOptionを作成するためのヘルパー。`bool_condition`がfalseの場合、関数`func`が引数なしで呼び出され、その結果が`Identity`にラップされます。`bool_condition`がtrueの場合、`Option()`が返されます。

正確には[`iftrue`](@ref)の逆です。
