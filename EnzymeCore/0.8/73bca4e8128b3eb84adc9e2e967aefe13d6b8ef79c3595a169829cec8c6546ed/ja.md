```
make_zero(::Type{T}, seen::IdDict, prev::T, ::Val{copy_if_inactive}=Val(false))::T
```

再帰的に型 `T` の値 `prev` のゼロコピーを作成します。引数 `copy_if_inactive` は、型 `T` が非アクティブであることが保証されている場合に何をするかを指定します。プライマルを使用する（デフォルト）か、それとも値をコピーし続けるかです。
