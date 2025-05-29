```
feedback(s1::NamedStateSpace, s2::NamedStateSpace;
        w1 = [],  u1 = (:), z1 = (:), y1 = (:),
        w2 = (:), u2 = (:), z2 = (:), y2 = [], kwargs...)
```

Feedback between two named systems. The lists of signals to connect are expected to be lists of symbols with signal names, `(:)` indicating all signals, or `[]` indicating no signals.

All signal sets `w1,u1,z1,y1,u2,y2,w2,z2` have the same meaning as for the advanced feedback methods for regular systems. The added signal set `r` is used to optionally provide a new name for the input of the feedback loop.

To simplify creating complicated feedback interconnections, see `connect`.

If not all inputs and outputs are connected, the returned system may not be a minimal realization. Use `sminreal` (possibly also `minreal`) to simplify the system if only the input-output map is of interest.
