```
frostdays(C::ClimGrid)
```

FD, Number of frost days: Annual count of days when TN (daily minimum temperature) < 0 Celsius.

Let TN[i,j] be daily minimum temperature on day i in year j. Count the number of days where:

TN[i,j] < 0 Celsius.
