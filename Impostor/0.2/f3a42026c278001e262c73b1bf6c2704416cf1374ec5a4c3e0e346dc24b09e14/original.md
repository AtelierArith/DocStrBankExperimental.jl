```
birthdate(n::Integer = 1; start::Date, stop::Date)
```

Generate `n` birth date entries between the `start` and `stop` dates.

# Parameters

  * `n::Int = 1`: number of dates to generate.
  * `start::Date = Date(1900, 1, 1)`: start of the sampling period.
  * `stop::Date = Dates.today()`: end of the sampling period.
