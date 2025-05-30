```julia
confirm(element::Any)
```

Normally, when you move a [`Slider`](@ref) or type in a [`TextField`](@ref), all intermediate values are sent back to `@bind`.

By wrapping an input element in `confirm`, you get a button to manually control when the value is sent, intermediate updates are hidden from Pluto.

One case where this is useful is a notebook that does a long computation based on a `@bind` input.

# Examples

```julia
@bind x confirm(Slider(1:100))

x == 1 # (initially)
```

Now, when you move the slider, nothing happens, until you click the `"Confirm"` button, and `x` is set to the new slider value.

> The result looks like:
>
> ![screenshot of running the code above in pluto](https://user-images.githubusercontent.com/6933510/145615211-2731f1f5-5c7d-4aac-9aa5-8afe89e24a6b.png)


# See also

You can combine this with [`PlutoUI.combine`](@ref)!

```julia
@bind speeds confirm(
	combine() do Child
		@htl("""
		<h3>Wind speeds</h3>
		<ul>
		$([
			@htl("<li>$(name): $(Child(name, Slider(1:100)))")
			for name in ["North", "East", "South", "West"]
		])
		</ul>
		""")
	end
)
```

> The result looks like:
>
> ![screenshot of running the code above in pluto](https://user-images.githubusercontent.com/6933510/145614965-7a1e8630-4766-4589-8a84-b022bdfb09fc.gif)

