A button that sends back the number of times that it was clicked.

You can use it to *trigger reactive cells*.

## Examples

In one cell:

```julia
@bind go CounterButton("Go!")
```

and in a second cell:

```julia
begin
	# reference the bound variable - clicking the button will run this cell
	go

	md"My favorite number is $(rand())!"
end
```
