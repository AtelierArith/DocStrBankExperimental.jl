```
on_new_rule(hook, frule | rrule)
```

新しいルールが定義されるときに実行される `hook` 関数を登録します。フックは入力としてシグネチャ型タイプを受け取り、一般的には `eval` を使用してADシステムのオーバーロードされた型のオーバーロードを定義します。例えば、シグネチャ型 `Tuple{typeof(+), Real, Real}` を使用して `+(::DualNumber, ::DualNumber)` が `frule` の `+` を呼び出すようにします。シグネチャ型タプルは常に次の形式を持ちます: `Tuple{typeof(operation), typeof{pos_arg1}, typeof{pos_arg2}...}`、ここで `pos_arg1` は最初の位置引数です。

フックは、パッケージがロードされるときに新しいルールに対して自動的に実行されます。手動でトリガーすることもできます [`refresh_rules`](@ref)。フックが `on_new_rule` で最初に登録されると、すべての既存のルールで実行されます。 ```
