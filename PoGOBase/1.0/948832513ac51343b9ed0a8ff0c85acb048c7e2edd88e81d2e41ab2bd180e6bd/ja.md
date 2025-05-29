```
base_stats(poke::Pokemon) → (a, d, h)
base_stats(species::Species; mega::Union{Bool, Char} = false) → (a, d, h)
```

ポケモンまたは種の基本攻撃（`a`）、防御（`d`）、スタミナ（`h`）のステータスを返します。`poke`がメガ進化であるか、`mega != false`の場合、メガ進化の基本ステータスが返されます。
