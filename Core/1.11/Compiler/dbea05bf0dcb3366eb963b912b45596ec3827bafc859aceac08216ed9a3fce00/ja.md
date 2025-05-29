```
is_immutable_argtype(argtype) -> Bool
```

`argtype`オブジェクトが不変であることが知られている場合は`true`を返します。このクエリは特に`getfield_effects`および`isdefined_effects`のために設計されており、不変オブジェクトに適用された`getfield` / `isdefined`呼び出しの`:consistent`-cyを証明することを可能にします。そうでない場合は、非不変オブジェクトがグローバルオブジェクトでないことを追加で証明する必要があります。これにより`:consistent`-cyを証明します。
