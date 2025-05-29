This module deals with controlling the cursor.

The two major pieces of functionality in this module are moving the cursor and hiding the cursor.

Move the cursor using the [`move!`](@ref) function:

```julia
move!(Up(3))
```

There are several different movements available, see documentation on the subtypes of [`Movement`](@ref) for more details.

It is possible to temporarily move the cursor to a different location using [`save`](@ref) or [`checkpoint`](@ref):

```julia
move!(Coordinate(1, 1))
println("First line!")

save() do
	move!(Down(4))
	println("Fifth line!")

	checkpoint() do
		move!(Down(4))
		println("Tenth line!")

		checkpoint() do
			move!(Down(4))
			println("Fifteenth line!")
		end
	end
end

println("Second line!")

checkpoint() do
	move!(Down(4))
	println("Sixth line!")

	checkpoint() do
		move!(Down(4))
		println("Eleventh line!")
	end
end
```

The location of the cursor can also be found using [`location`](@ref), though note that this only works in raw mode:

```julia-repl
julia> Screen.raw(Cursor.location)
Ansillary.Inputs.Location(0x003c, 0x0001)
```

Hiding the cursor is done using Julia's support for `do`-notation:

```julia-repl
julia> Cursor.hide() do
		   for c in "There is no cursor..."
			   print(c)
			   sleep(0.1)
		   end
	   end
There is no cursor...
```
