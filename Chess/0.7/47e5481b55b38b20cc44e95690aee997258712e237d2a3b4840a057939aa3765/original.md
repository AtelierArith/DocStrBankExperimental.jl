```
forward!(g::SimpleGame)
forward!(g::Game)
forward!(g::Game, m::Move)
forward!(g::Game, m::String)
```

Go one step forward in the game by replaying a previously retracted move.

If we're already at the end of the game, the game is unchanged. If the current node has multiple children, we always pick the first child (i.e. the main line). If any child other than the first child is desired, supply the move leading to the child node as the second argument. It's the caller's responsibility that the move supplied leads to one of the existing child nodes.
