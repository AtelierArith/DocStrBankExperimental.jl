```
tupled(Option(1), Option(2), Option(3)) == Option((1,2,3))
tupled(Option(1), None, Option(3)) == None
```

Combine several Applicative contexts by building up a Tuple
