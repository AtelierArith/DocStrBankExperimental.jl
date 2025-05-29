```
transform!(st::Monotonicer, features::T) where {T<:Union{Vector,Matrix,DataFrame}}
```

モノトニックまたは日次モノトニックデータを正規化するために、差分を取り、フリップをカウントします。
