```
player(game::Game{H,K}, h::H)
```

履歴 h におけるどのプレイヤーのターンであるかに対応する整数 ID を返します。0 - チャンス、1 - プレイヤー 1、2 - プレイヤー 2

IIE からマトリックスゲームに変換する場合は、次を実装する必要があります:     `player(game::Game{H,K}, k::K)`
