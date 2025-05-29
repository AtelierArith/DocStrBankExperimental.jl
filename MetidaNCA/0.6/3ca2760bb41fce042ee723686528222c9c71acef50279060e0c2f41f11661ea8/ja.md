```
applylimitrule!(f::Function, data::DataSet{T}, rule::LimitRule) where T <: Union{PKSubject, PDSubject}
```

`f(subj)` が `true` を返す場合に適用します。
