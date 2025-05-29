```
drawbezierpath(bps::BezierPathSegment;
    action=:none,
    close=false)
```

Bézierパスセグメントを描画し、`:none`、`:stroke`、`:fill`などのアクションを適用します。デフォルトでは、パスはオープンです。

TODO ブール値よりも有用なものを返す。
