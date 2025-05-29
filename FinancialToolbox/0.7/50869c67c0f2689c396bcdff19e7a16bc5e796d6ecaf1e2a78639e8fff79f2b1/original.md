Fraction of year between two Dates according the following convention

```
	yfr=yearfrac(Date1,Date2,basis)
```

Where:

```
	Date1 = Start date.
	Date2 = End date.
	basis = Integer representing the following conventions:
			- 0 = (ACT/ACT)
			- 1 = (30/360 SIA)
			- 2 = (ACT/360)
			- 3 = (ACT/365)
			- 4 = (30/360 PSA)
			- 5 = (30/360 ISDA)
			- 6 = (30E/360)
			- 7 = (ACT/365 JPN)

	yfr      = fraction of year between start and end date according to basis.
```

# Example

```julia-repl
julia> yearfrac(Date(1996,10,12),Date(1998,1,10),1)
1.2444444444444445
```
