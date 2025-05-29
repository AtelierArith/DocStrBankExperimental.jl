```
findzero(f, bracket; atol=1e-7, max_iter=100)
findzero(f, method::AbstractBisection; atol=1e-7, max_iter=100)
```

渡されたメソッドを使用して根を見つけます。メソッドを指定せずにブレケットが渡された場合は、[`Secant`](@ref) メソッドを使用します。
