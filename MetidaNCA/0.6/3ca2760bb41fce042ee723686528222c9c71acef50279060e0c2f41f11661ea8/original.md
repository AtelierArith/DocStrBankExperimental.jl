```
applylimitrule!(f::Function, data::DataSet{T}, rule::LimitRule) where T <: Union{PKSubject, PDSubject}
```

Apply if `f(subj)` return  `true`.
