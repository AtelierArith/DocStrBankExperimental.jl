```
squared_transfer(f, sdof::Oscillator)
```

Compute the square of the transfer function for a SDOF system, `sdof`, at frequency `f`.

# Examples

```julia-repl
	f = 2.0
	# create sdof with natural frequency f_n=1.0 and damping ζ=0.05
	sdof = Oscillator( 1.0, 0.05 )
	Hf2 = squared_transfer( f, sdof )
```

See also: [`transfer`](@ref)
