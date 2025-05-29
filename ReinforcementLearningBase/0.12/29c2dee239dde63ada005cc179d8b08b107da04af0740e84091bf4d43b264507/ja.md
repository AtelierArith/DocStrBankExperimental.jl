```
current_player(env)
```

次に行動を取るプレイヤーを返します。[拡張形式ゲーム](https://en.wikipedia.org/wiki/Extensive-form_game)では、*チャンスプレイヤー*が返される場合があります。（[`chance_player`](@ref)も参照）[同時](@ref)環境では、*同時プレイヤー*が常に返されます。（[`simultaneous_player`](@ref)も参照）。
