```
base_stats(poke::Pokemon) → (a, d, h)
base_stats(species::Species; mega::Union{Bool, Char} = false) → (a, d, h)
```

Return the base attack (`a`), defense (`d`), and stamina (`h`) stats for a `Pokemon` or `Species`. If `poke` is a mega-evolution or `mega != false`, the base stats for the mega-evolution are returned.
