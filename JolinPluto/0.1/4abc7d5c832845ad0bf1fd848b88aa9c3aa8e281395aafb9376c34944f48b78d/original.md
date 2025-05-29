```julia
viewof(:symbol, element)
viewof("symbol", element)
```

Return the HTML `element`, and use its latest JavaScript value as the definition of `symbol`.

# Example

```julia
viewof(:x, html"<input type=range>")
```

and in another cell:

```julia
x^2
```

The first cell will show a slider as the cell's output, ranging from 0 until 100. The second cell will show the square of `x`, and is updated in real-time as the slider is moved.
