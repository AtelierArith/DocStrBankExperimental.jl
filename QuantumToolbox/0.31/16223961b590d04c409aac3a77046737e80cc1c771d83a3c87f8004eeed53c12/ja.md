```
w_state(n::Union{Int,Val})
```

`n`-量子ビットの[W状態](https://en.wikipedia.org/wiki/W_state)を返します：

$$
\frac{1}{\sqrt{n}} \left( |100...0\rangle + |010...0\rangle + \cdots + |00...01\rangle \right)
$$

!!! warning "型の安定性に注意！"
    型の安定性を保ちたい場合は、`w_state(n)`の代わりに`w_state(Val(n))`を使用することをお勧めします。詳細については、[このリンク](https://docs.julialang.org/en/v1/manual/performance-tips/#man-performance-value-type)と[関連セクション](@ref doc:Type-Stability)を参照してください。

