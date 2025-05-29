```
isnegative(sol::ODESolution)
```

`sol.u` に負の要素が含まれている場合は `true` を返します。

解をプロットする際に使用される補間によっては、負の値が発生する可能性があることに注意してください。

[`isnonnegative`](@ref) も参照してください。
