```
convert_thresholds
```

Converts threshold input into Threshold intervals. Intervals are created for each tuple in the input. All intervals are halfopen. When the direction is up they are closed on the lower bound and open on the upper bound. When the direction is down they are open on the lower bound and closed on the upper bound. The lowest bound is always 0 and the highest bound is always 1. The edges 0 and 1 are always closed.
