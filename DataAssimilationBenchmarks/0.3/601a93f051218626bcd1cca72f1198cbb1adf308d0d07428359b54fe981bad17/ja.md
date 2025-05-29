```
function ConM(type)
    Union{UniformScaling{T}, Symmetric{T}} where T <: type
end
```

最適化ルーチンで使用される条件付き行列タイプの型の和。これはtransformメソッドで使用されます。
