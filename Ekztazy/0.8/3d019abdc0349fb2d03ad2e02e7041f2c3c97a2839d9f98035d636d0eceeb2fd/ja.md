```
command!(
    f::Function
    c::Client
    name::AbstractString
    description::AbstractString;
    kwargs...
)
```

INTERACTION CREATEゲートウェイイベントのハンドラーを追加します。ここで、InteractionDataの`name`フィールドが`name`と一致します。このコマンドは、`guild`の存在に基づいて`c.commands`または`c.guild_commands`に追加されます。`f`パラメータのシグネチャは次のようにする必要があります。

```
    (ctx::Context, args...) -> Any 
```

ここで、argsはすべてのコマンドオプションのリストです。

たとえば、ユーザーuと数値nを入力として受け取るコマンドは、次のシグネチャを持つ必要があります。

```
(ctx::Context, u::User, n::Int) -> Any
```

引数は自動的に変換されます。

**注意:** 引数名は**必ず**オプション名と一致する必要があります。引数は任意の順序で配置できます。型が指定されていない場合、変換は行われないため、Discordオブジェクトは`Snowflake`になります。
