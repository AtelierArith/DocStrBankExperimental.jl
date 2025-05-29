```
walkpath(g, paths, start; dir=:out, stopcond=(g,v)->false)
```

与えられた `paths` に沿って `start` から歩き、最後のノードを返します。`dir` が指定されている場合は、対応するエッジの方向を使用します（`:in` と `:out` が許可される値です）。
