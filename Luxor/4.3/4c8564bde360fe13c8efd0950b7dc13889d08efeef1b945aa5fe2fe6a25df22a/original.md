```
Push(t::Turtle)
```

Save the turtle's position and orientation on the stack. 

Use `Pop()` to restore this position and orientation from the top value on the stack, discarding the current position and orientation.

Turtles can be sociable creatures; there's just one stack, and it's shared by all turtles, So it's possible for one turtle to pop the stack values that were `pushed` by another turtle.
