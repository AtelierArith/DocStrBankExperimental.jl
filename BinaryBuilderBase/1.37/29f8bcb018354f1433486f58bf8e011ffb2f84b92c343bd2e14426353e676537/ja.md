```
satisfied(p::Product;
          platform::AbstractPlatform = HostPlatform(),
          verbose::Bool = false,
          isolate::Bool = false)
```

与えられた [`Product`](@ref) に対して、その `Product` が満たされている場合は `true` を返します。つまり、その `Product` に設定されたすべての基準に一致するファイルが存在するかどうかです。`isolate` が `true` に設定されている場合、`dlopen()` によってライブラリを読み込むことが問題を引き起こす可能性がある場合に、すべてのチェックをメインの Julia プロセスから隔離します。
