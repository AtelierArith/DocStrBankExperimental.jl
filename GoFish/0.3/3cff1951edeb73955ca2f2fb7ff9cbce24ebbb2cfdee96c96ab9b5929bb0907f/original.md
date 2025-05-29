```
Game{T} <: AbstractGame{T}
```

A Go Fish game object where `T` is the player id type.

# Fields

  * `deck`: deck of cards
  * `book`: a dictionary containing player id and card value:  `id => value`
  * `hand_size`: maximum number of cards in each player's hand
