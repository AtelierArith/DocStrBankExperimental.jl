```
Pop(t::Turtle)
```

Get the position and orientation off the stack, as previously saved with `Push()`, and set the turtle to those values, discarding the current position and orientation.

Turtles can be sociable creatures; there's just one stack, and it's shared by all turtles, So it's possible for one turtle to pop the stack values that were `pushed` by another turtle. 
