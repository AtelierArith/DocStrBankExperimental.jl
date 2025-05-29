```
OnSpawn
```

アクターのライフサイクルメッセージで、アクターの最初のスケジューリングを示し、他のメッセージの前に生成中に送信されます。

# 例

```julia
CircoCore.onmessage(me::MyActor, ::OnSpawn, service) = begin
    registername(service, "MyActor", me) # このアクターをローカル名前サービスに登録します
end
```
