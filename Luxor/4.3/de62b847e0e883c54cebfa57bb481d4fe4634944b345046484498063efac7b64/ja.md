```
drawbezierpath(bezierpath::BezierPath, action=:none;
    close=true)
drawbezierpath(bezierpath::BezierPath;
    action=:none,
    close=true)
```

Bézierパスを描画し、`:none`、`:stroke`、`:fill`などのアクションを適用します。デフォルトでは、パスは閉じています。

TODO ブール値よりも有用なものを返す。
