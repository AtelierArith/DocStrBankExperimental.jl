```
takearray!(v::CeedVector, mtype::MemType)
```

[`CeedVector`](@ref) 配列の所有権を取得し、配列を [`CeedVector`](@ref) から削除します。呼び出し元は配列の管理と解放を行う責任があります。配列は `Ptr{CeedScalar}` として返されます。
