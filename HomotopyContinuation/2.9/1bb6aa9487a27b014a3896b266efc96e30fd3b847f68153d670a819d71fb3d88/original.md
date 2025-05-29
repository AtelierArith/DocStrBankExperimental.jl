```
EndgameTracker(tracker::Tracker; options = EndgameOptions())
EndgameTracker(H::AbstractHomotopy; options = EndgameOptions())
```

A `EndgameTracker` combines a [`Tracker`](@ref) with an endgame. That is, while a [`Tracker`](@ref) assumes that the solution path is non-singular and convergent, the endgame allows to handle singular endpoints as well as diverging paths. To compute singular solutions the *Cauchy endgame* used, for divering paths a strategy based on the valuation of local Puiseux series expansion of the path is used. By convention, a `EndgameTracker` always tracks from $t=1$ to $t = 0$. See [`EndgameOptions`](@ref) for the possible options.
