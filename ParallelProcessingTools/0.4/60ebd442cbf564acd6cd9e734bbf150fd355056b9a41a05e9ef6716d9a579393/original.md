```
@userfriendly_exceptions expr
```

Transforms exceptions originating from `expr` into more user-friendly ones.

If multiple exceptions originate from parallel code in `expr`, only one is rethrown, and `TaskFailedException`s and `RemoteException`s are replaced by the original exceptions that caused them.

See [`inner_exception`] and [`onlyfirst_exception`](@ref).
