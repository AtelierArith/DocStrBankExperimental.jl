```
Life(brt::BasicRateTable,a,d)
```

This function returns a random variable that correspond to an extracted Life from the `BasicRateTable` at age `a` and date `d`. 

This works by checking if the individual is closer to the oldest age than the last year in the ratetable, calculating at each step the time difference and the hazard values. For the younger individuals, we assume they go through the last column at the end no matter what age they are. 
