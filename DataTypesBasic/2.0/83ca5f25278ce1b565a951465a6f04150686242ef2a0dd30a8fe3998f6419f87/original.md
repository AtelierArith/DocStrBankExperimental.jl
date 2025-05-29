```
flip_left_right(Const(1)) == Identity(1)
flip_left_right(Identity(:whatever)) == Const(:whatever)
```

exchanges left and right, i.e. what was Const, becomes an Identity and the other way around.
