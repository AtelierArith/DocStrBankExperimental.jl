```
mid(a::Interval, α=0.5)
```

Find an intermediate point at a relative position `α``in the interval`a`. The default is the true midpoint at`α = 0.5`.

Assumes 0 ≤ α ≤ 1.

Warning: if the parameter `α = 0.5` is explicitly set, the behavior differs from the default case if the provided `Interval` is not finite, since when `α` is provided `mid` simply replaces `+∞` (respectively `-∞`) by `prevfloat(+∞)` (respecively `nextfloat(-∞)`) for the computation of the intermediate point.
