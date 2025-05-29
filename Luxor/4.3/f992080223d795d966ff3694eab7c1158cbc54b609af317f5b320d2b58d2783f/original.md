```
drawbezierpath(bps::BezierPathSegment;
    action=:none,
    close=false)
```

Draw the Bézier path segment, and apply the action, such as `:none`, `:stroke`, `:fill`, etc. By default the path is open.

TODO Return something more useful than a Boolean.
