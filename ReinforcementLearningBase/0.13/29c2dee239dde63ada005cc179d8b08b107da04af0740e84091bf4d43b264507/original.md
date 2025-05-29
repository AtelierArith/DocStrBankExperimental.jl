```
current_player(env)
```

Return the next player to take action. For [Extensive Form Games](https://en.wikipedia.org/wiki/Extensive-form_game), a *chance player* may be returned. (See also [`chance_player`](@ref)) For [SIMULTANEOUS](@ref) environments, a *simultaneous player* is always returned. (See also [`simultaneous_player`](@ref)).
