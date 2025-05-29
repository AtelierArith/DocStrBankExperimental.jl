```
get_variable_description(label::Symbol, database::TelemetryDatabase) -> TelemetryVariableDescription
```

`database`内の`label`を持つ変数の説明を取得します。`label`は変数のエイリアスでもあることに注意してください。変数が見つからない場合、関数は`nothing`を返します。
