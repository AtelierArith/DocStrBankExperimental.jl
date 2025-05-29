```
is_power(a::T, n::Int) where T <: Integer
```

$ a $ が完璧な $ n $ 乗であり、$ a = q^n $ である場合は `true, q` を返します。そうでない場合は `false, 0` を返します。$ n > 0 $ であることが必要です。
