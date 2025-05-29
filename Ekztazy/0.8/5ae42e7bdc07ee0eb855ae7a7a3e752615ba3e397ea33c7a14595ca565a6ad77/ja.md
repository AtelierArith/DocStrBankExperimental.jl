```
update_status(
    c::Client,
    since::Nullable{Int},
    activity::Nullable{Activity},
    status::Union{PresenceStatus, AbstractString},
    afk::Bool,
) -> Bool
```

プレゼンスまたはステータスの更新を示します。`PresenceUpdate` イベントは、ゲートウェイによって応答として送信されます。詳細は[こちら](https://discordapp.com/developers/docs/topics/gateway#update-status)を参照してください。
