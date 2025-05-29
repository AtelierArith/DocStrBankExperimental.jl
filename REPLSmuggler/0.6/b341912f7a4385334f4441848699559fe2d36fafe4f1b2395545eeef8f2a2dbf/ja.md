```
smuggle([name]; basepath=basepath(), serializer=MsgPack)
```

UNIXソケットを使用してランダムな名前でサーバーを起動し、`MsgPack.jl`をシリアライザーとして使用します。ソケットは`joinpath(basepath, name)`に保存されます。`name`が提供されていない場合、REPLSmugglerは既存のソケット名でないランダムに生成された名前を試みます。

例えば、Linuxでは、名前が`clandestine_underworld`に選ばれた場合、ソケットは`/run/user/1000/julia/replsmuggler/clandestine_underworld`に見つけることができます。

ソケット名はREPLに表示され、サーバーは[`CURRENT_SMUGGLER`](@ref)を通じてアクセス可能です。

また、[basepath](@ref)も参照してください。
