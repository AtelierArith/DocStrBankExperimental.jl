```
has(elm::Element, tr::Transition)::Bool
```

指定された要素に対して指定された遷移が利用可能ですか？

例:

```
@assert has(n"Fe L3-M5)
@assert !has(n"Fe N7-O9)
```
