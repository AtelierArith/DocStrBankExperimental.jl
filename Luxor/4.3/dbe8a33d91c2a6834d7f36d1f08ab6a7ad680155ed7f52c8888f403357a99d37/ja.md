```
ellipse(focus1::Point, focus2::Point, pt::Point;
    action=:none,
    stepvalue=pi/100,
    vertices=false,
    reversepath=false)
```

2つの点と楕円上の点を与えられたときに、楕円の多角形近似を構築します。
