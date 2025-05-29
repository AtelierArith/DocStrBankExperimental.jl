```
add_segment!(e::Envelop, l::Line)
```

Adds a new line segment to an envelop based on the value of its slope (slopes must be decreasing always in the envelop). The cutpoints are automatically determined by intersecting the line with the adjacent lines.
