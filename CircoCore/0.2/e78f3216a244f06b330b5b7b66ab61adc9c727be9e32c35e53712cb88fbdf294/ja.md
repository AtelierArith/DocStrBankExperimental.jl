```
registername(service, name::String, actor::Union{Addr,Actor})
```

指定された名前でスケジューラーローカルの名前レジストリに指定されたアクターを登録します。

移行や死亡時に名前を登録解除する必要はありません。

# TODO 手動および自動登録解除の実装
