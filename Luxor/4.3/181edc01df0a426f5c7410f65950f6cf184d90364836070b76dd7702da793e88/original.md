```
blend(from::Point, to::Point)
```

Create an empty linear blend.

A blend is a specification of how one color changes into another. Linear blends are defined by two points: parallel lines through these points define the start and stop locations of the blend. The blend is defined relative to the current axes origin. This means that you should be aware of the current axes when you define blends, and when you use them.

To add colors, use `addstop()`.
