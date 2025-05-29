```
add_drivers_to_cache(p::NamedTuple, model::AbstractModel, coords)
```

ドライバ変数のNamedTuple（大気および放射強制など）を作成し、それをキー`drivers`の下で`p`にマージします。ドライバ変数が必要ない場合、`p`は変更されずに返されます。
