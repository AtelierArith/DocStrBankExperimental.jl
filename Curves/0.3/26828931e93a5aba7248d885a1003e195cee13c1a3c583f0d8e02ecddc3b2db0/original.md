```
get_tenor(x:: Integer):: Tenor
```

Converts the given number of days to a Tenor.

The following mapping is used (exactly the reverse of `get_days`): TDays => 1, TWeeks => 7, TMonths => 30, TYears => 365
