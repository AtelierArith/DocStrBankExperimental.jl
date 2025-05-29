```
PartialNamedTuple(::NamedTuple)
```

Wraps a NamedTuple to signal an EpisodesBuffer that it is pushed into that it should ignore the fact that this is a partial insertion. Used at the end of an episode to complete multiplex traces before moving to the next episode.
