```
GameHeaders
```

Type representing the PGN header tags for a game.

Contains a slot for each the seven required PGN tags `event`, `site`, `date`, `round`, `white`, `black` and `result`, all of which are strings. Remaining tags are included in the `othertags` slot, which contains a vector of `GameHeader`s.
