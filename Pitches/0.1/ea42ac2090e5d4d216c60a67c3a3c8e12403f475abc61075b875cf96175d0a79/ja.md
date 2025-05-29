```
abstract type IntervalClass <: Interval end
```

任意の区間クラス型は `IntervalClass` のサブタイプであるべきです。区間に関するメソッドに加えて、区間クラスは以下を実装する必要があります：

  * `embed`
  * `intervaltype(T)`

`intervalclasstype(T)` と `ic` は同一であるべきです。
