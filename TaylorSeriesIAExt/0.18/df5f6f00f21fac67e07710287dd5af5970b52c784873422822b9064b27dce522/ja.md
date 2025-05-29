```
normalize_taylor(a::Taylor1, I::Interval, symI::Bool=true)
```

`a::Taylor1`を正規化し、区間`I`がアフィン変換によって区間`-1..1`（`symI=true`）または`0..1`（`symI=false`）にマッピングされるようにします。
