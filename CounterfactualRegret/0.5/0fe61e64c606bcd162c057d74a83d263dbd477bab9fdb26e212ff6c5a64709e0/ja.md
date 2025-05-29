```
infokey(game::Game, h)
```

情報セットに対応する一意の識別子を返します

`infokey(game, h1) == infokey(game, h2)` ⟺ h1 と h2 は同じ情報セットに属します

（キーは辞書のキーとして保存されるため、不変でなければなりません）
