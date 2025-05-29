```
catmullrom_by_arclength( points )    
catmullrom_by_arclength( points, (min_between_points, max_between_points))
```

Calculates a Catmull-Rom fit through given `points`, where the number of interpoint knots varys inversely with the approximate arclength of that arc.

`arcpoints_min` and `arcpoints_max` refer any one arc between two points.
