```
startboard960(i=nothing)
```

Returns a `Board` object with a Chess960 starting position.

The optional parameter `i` – an integer in the range 0..959 – is used to pick a particular Chess960 position, using the indexing scheme described [here](https://en.wikipedia.org/wiki/Fischer_random_chess_numbering_scheme). When this parameter is omitted, the function picks a random position.
