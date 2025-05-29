```
@envelope(arguments...)
```

Create an envelope. Start with the start amplitude (a number between 0 and 1). Then, specify a pair, `segment_function` => `duration`, where `duration` is the duration of the segment. Then, specify the end amplitude (again, a number between 0 and 1). So for example,

For example, `@envelope(0, Line => 1s, 1)` will create an envelope with 1 segment. The segment is created with `segment_function(start_level, duration, end_level) => duration`. So, for this example, the segment will be `Line(0, 1s, 1) => 1s`.

After you finished your first segment, you can add as many more segments as you'd like. The end level of the previous segment will be the start level of the next segment.

For example, `@envelope(0, Line => 1s, 1, Line => 1s, 0)` will create an envelope with 2 segments:

1. `Line(0, 1s, 1) => 1s`
2. `Line(1, 1s, 0) => 1s`

```jldoctest
julia> using AudioSchedules

julia> @envelope(0, Line => 1s, 1, Line => 1s, 0)
(Line(0.0, 1.0 s⁻¹) => 1.0 s, Line(1.0, -1.0 s⁻¹) => 1.0 s)

julia> @envelope(1, 2, 3)
ERROR: LoadError: ArgumentError: 2 is not a pair
[...]
```
