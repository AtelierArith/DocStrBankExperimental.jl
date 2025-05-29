```
shift_start(ptr::Ptr, i::Integer)
```

指定されたiの要素数だけポインタをシフトします。別の呼び出し方は`ptr << nof_elements`を使用することです。使用例:

```julia-repl
julia> a = [1,2,3,4]
julia> pt = Pointer(a)
julia> pt[1]
1
julia> pt = pt << 2
julia> pt[1]
3
```
