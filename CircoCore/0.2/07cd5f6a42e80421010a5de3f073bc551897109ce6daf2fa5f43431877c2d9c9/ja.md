```
Addr(postcode::PostCode, box::ActorId)
Addr(readable_address::String)
Addr()
```

アクターの完全なアドレス。

引数なしで作成された場合、それはヌルアドレスになります。 [`isnulladdr()`](@ref) を参照してください。

参照されたアクターが別のスケジューラに移動すると、古いアドレスに送信されたメッセージは [`RecipientMoved`](@ref) として戻ってきますので、Addrは手動で更新する必要があります。

# 例

Addr("192.168.1.11:24721", 0xbc6ac81fc7e4ea2)

Addr("192.168.1.11:24721/bc6ac81fc7e4ea2")
