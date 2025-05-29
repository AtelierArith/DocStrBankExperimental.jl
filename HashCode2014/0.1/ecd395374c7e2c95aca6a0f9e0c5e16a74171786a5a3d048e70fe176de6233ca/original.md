```
is_feasible(solution, city[; verbose=false])
```

Check if `solution` satisfies the constraints for the instance defined by `city`. The following criteria are considered (taken from the problem statement):

  * the number of itineraries has to match the number of cars of `city`
  * the first junction of each itinerary has to be the starting junction of `city`
  * for each consecutive pair of junctions on an itinerary, a street connecting these junctions has to exist in `city` (if the street is one directional, it has to be traversed in the correct direction)
  * the duration of each itinerary has to be lower or equal to the total duration of `city`
