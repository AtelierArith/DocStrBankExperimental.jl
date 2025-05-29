```
intersectboxes(box1::AbstractVector, box2::AbstractVector)
```

2つのボックスの交差を計算します。

交差が空である場合、関数は空のボックス（length(b) == 0）を返します。そうでない場合は、ボックスが返されます。
