```
set_flags!(c::Calculation, flags::Pair{Symbol, Any}...; print=true, force=false)
```

複数のフラグを一度に設定します。フラグの有効性と型が検証されます。

```
set_flags!(job::Job, calculations::Vector{<:Calculation}, flags::Pair{Symbol,<:Any}...; print=true)
set_flags!(job::Job, flags::Pair{Symbol,<:Any}...; print=true)
```

名前に指定されたフラグを設定します。これは、指定されたフラグが名前に対して有効な場合にのみ行われます。
