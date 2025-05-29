```
minimum(interval::AbstractInterval{T}; [increment]) -> T
```

`interval` に含まれる最小値。

左閉区間の場合、`first(interval)` を返します。左開区間の場合、`first(interval) + eps(first(interval))` を返します。左無限大の場合、型 `T` に対して可能な最小値を返します。

空の区間や、インクリメントが区間に含まれない最小値をもたらす場合には `BoundsError` がスローされます。
