```
normalize_taylor(a::TaylorN, I::IntervalBox, symI::Bool=true)
```

`a::TaylorN`を正規化して、`I::IntervalBox`内の区間がアフィン変換によって区間`-1..1`（`symI=true`）または`0..1`（`symI=false`）にマッピングされるようにします。
