```
create_independent(x::Union{Cdouble, Vector{Cdouble}}, param::Union{Cdouble,Vector{Cdouble}})
```

引数 `x` は微分可能な `Adouble{TbAlloc}` として保存され、独立としてマークされます。`param` はテープ上のパラメータとしてマークされ、再テープなしで変更可能です。
