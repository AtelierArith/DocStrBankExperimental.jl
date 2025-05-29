```
initialise_introspected_struct([client::Client], name::String)
initialise_introspected_struct([client::Client], name::SubString)
initialise_introspected_struct(T::Type)
```

すべてのフィールドがnothingに設定されたイントロスペクション構造体を初期化します。文字列として供給された型の名前がある場合、これは`client.introspected_types`から`Type`を取得します。
