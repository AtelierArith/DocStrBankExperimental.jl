```
get_attribute(f::Function, G::Any, attr::Symbol)
```

属性 `attr` に保存されている値を返します。値が設定されていない場合は、`f()` を返します。

これは `do` ブロック構文を使用して呼び出すことを意図しています。

```julia
get_attribute(obj, attr) do
    # 必要に応じてここでデフォルト値を計算
    ...
end
```
