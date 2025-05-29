```
shiftbezierhandles(bps::BezierPathSegment;
    angles=[0.1, -0.1],
    handles=[1.1, 1.1])
```

Return a new BezierPathSegment that modifies the Bézier path in `bps` by moving the control handles. The values in `angles` increase the angle of the handles; the values in `handles` modifies the lengths: 1 preserves the length, 0.5 halves the length of the  handles, 2 doubles them.
