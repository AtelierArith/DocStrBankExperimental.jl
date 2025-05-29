```
go_game_graph(board_graph::Graphs.SimpleGraph)
```

Return the directed graph corresponding to playing the game of go on the undirected graph `board_graph`. Although go is traditionally played on a square grid, the rules can be applied to any undirected graph. All the possible board positions act as vertices in the game graph and the moves as edges. The empty board corresponds to vertex 1. The result is a sparse directed and strongly connected graph with lots of cycles. It is returned as a `Graphs.SimpleDiGraph`.

The size of the game graph grows exponentially with the number of vertices in the corresponding board graph. This function supports board graphs of up to 12 vertices. The size limit can be overridden but you have been warned.

```
go_game_graph(board_graph::SimpleGraph; allow_self_capture = false)
```

The keyword argument `allow_self_capture` can be set to `false` to disallow moves that causes the player to lose his own stones. This results in a game graph with fewer edges than when self captures are allowed.

(Side note: all variations of go rules agree on the mechanics of playing moves but can have different opinions about which moves are valid. Whether to allow multi-stone self captures is one such difference. However, all go rules agree that single-stone self captures are invalid since that would not change the position. In graph terms that means no self-edges, regardless of the setting of `allow_self_capture`.)

```
go_game_graph(n::Integer; kwargs...)
```

Shortcut for `go_game_graph(go_board_graph(n); kwargs...)`.
