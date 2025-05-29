Display a full-screen confetti animation! The confetti will disappear automatically, and it will be fired every time the cell is re-run.

# Example

You can trigger this to celebrate a correct answer:

```julia
# make x a very large number
x = 5
```

The next cell would be hidden:

```julia
if x > 1000000
	confetti()
end
```

Note that `confetti()` "returns the confetti launcher", which should be the output value of a cell. So this will work:

```julia
let
	x = 1
	y = x + 2
	if y == 3
		confetti()
	end
end
```

But this will not:

```julia
let
	x = 1
	y = x + 2
	if y == 3
		confetti()
	end
	y
end
```
