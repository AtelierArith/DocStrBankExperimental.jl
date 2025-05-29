```
reverse_dim!(var::OutputVar, dim_name)
```

[`reverse_dim`](@ref)と同様ですが、`var`内でインプレースで操作します。

この関数は、次元の順序を逆にする必要がある場合に役立ち、補間関数を作成できるようにします。
