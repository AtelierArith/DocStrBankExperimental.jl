```
trimbezier(bps::BezierPathSegment, lowpt, highpt)
```

BezierPathSegmentの端を`lowpt`と`highpt`で切り取ります。`lowpt`と`highpt`は0と1の間である必要があります。

切り取られたBezierPathSegmentを返します。
