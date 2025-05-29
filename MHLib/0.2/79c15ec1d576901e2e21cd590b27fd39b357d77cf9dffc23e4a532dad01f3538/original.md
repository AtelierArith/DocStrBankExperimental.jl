```
MHMethodStatistics
```

Struct that collects data on the applications of a `MHMethod`.

Attributes

  * `applications`: number of applications of this method
  * `netto_time`: accumulated time of all applications of this method without further costs   (e.g., VND)
  * `successes`: number of applications in which an improved solution was found
  * `obj_gain`: sum of gains in the objective values over all successful applications
  * `brutto_time`: accumulated time of all applications of this method including further   costs (e.g., VND)
