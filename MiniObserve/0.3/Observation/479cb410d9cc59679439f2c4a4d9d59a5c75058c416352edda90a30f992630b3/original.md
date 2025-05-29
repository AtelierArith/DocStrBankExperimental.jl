```Julia
@observe(statstype, user_arg1 [, user_arg2...], declarations)
```

Generate a full analysis and logging suite for a set of data structures.

Observe expects a (new) type name, a number of user arguments and a block of declarations. It will generate a function `observe` that takes the user arguments and returns an instance of the data type. The declaration block will be copied verbatim to the body of the `observe` function, but all occurences of the "pseudo-macros" `@record` and `@stat` will be replaced with corresponding analysis code. 

The newly defined result data type will contain properties for all calculated results.

So, given a declaration

```Julia
@observe Data model stat1 stat2 begin
	@record "time"      model.time
	@record "N"     Int length(model.population)

	for ind in model.population 
		@stat("capital", MaxMinAcc{Float64}, MeanVarAcc{FloatT}) <| ind.capital
		@stat("n_alone", CountAcc)           <| has_neighbours(ind)
	end

	@record s1			stat1
	@record s2			stat1 * stat2
end
```

a type Data will be generated that provides (at least) the following members:

```Julia
struct Data
	time :: Float64
	N :: Int
	capital :: @NamedTuple{max :: Float64, min :: Float64, mean :: Float64, var :: Float64}
	n_alone :: @NamedTuple{N :: Int}
	s1 :: Float64
	s2 :: Float64
end
```

The macro will also create a method `observe(::Type{Data), model, stat1, stat2)` that will perform the required calculations and returns a `Data` object. 

Use `print_header` to print a header for the generated type to an output and `log_results` to print the content of a data object.
