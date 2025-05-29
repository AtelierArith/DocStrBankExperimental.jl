```
set_param!(ref::ComponentReference, name::Symbol, value)
```

コンポーネントパラメータを `set_param!(reference, name, value)` として設定します。これにより、モデルのモデルパラメータリストにユニークな名前 :compname_paramname が作成され、参照されたコンポーネント内でのみそのパラメータがその値に設定されます。
