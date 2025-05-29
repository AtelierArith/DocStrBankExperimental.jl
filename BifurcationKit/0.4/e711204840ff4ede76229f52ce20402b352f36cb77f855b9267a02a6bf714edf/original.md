```
`FoldDetectEvent`
```

This event implements the detection of Fold points based on the p-component of the tangent vector to the continuation curve. It is designed to work with `PALC(tangent = Bordered())` as continuation algorithm. To use it, pass `event = FoldDetectEvent` to `continuation`.
