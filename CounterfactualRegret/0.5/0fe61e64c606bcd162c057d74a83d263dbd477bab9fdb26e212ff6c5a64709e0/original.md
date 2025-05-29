```
infokey(game::Game, h)
```

Returns unique identifier corresponding to some information set 

`infokey(game, h1) == infokey(game, h2)` ⟺ h1 and h2 belong to the same info set 

(key must be immutable as it's being stored as a key in a dictionary)
