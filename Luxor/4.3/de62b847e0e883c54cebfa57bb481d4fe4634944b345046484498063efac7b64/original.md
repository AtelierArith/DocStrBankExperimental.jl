```
drawbezierpath(bezierpath::BezierPath, action=:none;
    close=true)
drawbezierpath(bezierpath::BezierPath;
    action=:none,
    close=true)
```

Draw the Bézier path, and apply the action, such as `:none`, `:stroke`, `:fill`, etc. By default the path is closed.

TODO Return something more useful than a Boolean.
