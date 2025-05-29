```
seasonalyagg(A::ClimArray, f = mean) -> B
```

Create a new array where the temporal information has been aggregated into seasons using the function `f`. By convention, seasons are represented as Dates spaced 3-months apart, where only the months December, March, June and September are used to specify the date, with day 1.
