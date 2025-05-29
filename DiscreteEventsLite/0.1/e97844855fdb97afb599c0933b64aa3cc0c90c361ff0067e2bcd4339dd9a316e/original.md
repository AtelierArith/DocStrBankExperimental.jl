remove_events!: remove events by id  -`s`: scheduler

  * `until`: run until
  * `f`: removal function. Defaults to exact match.

Function signiture:

```julia
remove_events!(scheduler, id, f=(x,id)->x.first.id == id)
```
