```
send_after(lk::Link, time::Real, msg...)
```

[`Send`](@ref send) メッセージ `msg...` をアクター `lk` (または登録された `name`) に `time` 秒後に送信します。
