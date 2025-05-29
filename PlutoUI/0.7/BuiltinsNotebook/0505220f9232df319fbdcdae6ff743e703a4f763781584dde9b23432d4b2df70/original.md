A button that sends back the same value every time that it is clicked.

You can use it to *trigger reactive cells*.

**See also [`CounterButton`](@ref)** to get the *number of times* the button was clicked.

## Examples

In one cell:

```julia
@bind go Button("Go!")
```

and in a second cell:

```julia
begin
	# reference the bound variable - clicking the button will run this cell
	go

	md"My favorite number is $(rand())!"
end
```
