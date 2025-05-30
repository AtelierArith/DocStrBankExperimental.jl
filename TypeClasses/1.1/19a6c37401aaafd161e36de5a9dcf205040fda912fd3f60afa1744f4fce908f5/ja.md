```
tupled(Option(1), Option(2), Option(3)) == Option((1,2,3))
tupled(Option(1), None, Option(3)) == None
```

複数のApplicativeコンテキストを組み合わせてタプルを構築します。
