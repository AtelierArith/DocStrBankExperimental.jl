```
maximum(interval::AbstractInterval{T}; [increment]) -> T
```

`interval` に含まれる最大値。

右閉区間の場合、`last(interval)` を返します。右開区間の場合、`first(interval) + eps(first(interval))` を返します。右無限の場合、型 `T` に対して可能な最大値を返します。

空の区間や、インクリメントが区間に含まれない最大値をもたらす場合、`BoundsError` がスローされます。
