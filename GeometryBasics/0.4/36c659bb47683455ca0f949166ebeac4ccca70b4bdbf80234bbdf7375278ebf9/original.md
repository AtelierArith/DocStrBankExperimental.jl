```
in(b1::Rect, b2::Rect)
```

Check if Rect `b1` is contained in `b2`. This does not use strict inequality, so Rects may share faces and this will still return true.
