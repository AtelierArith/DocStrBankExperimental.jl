```
solution_summary(model::Model; verbose::Bool = false)
```

解の要約を印刷するために使用できる構造体を返します。

`verbose=true` の場合、空の名前を持つ変数を除いて、すべての変数のプライマル解とすべての制約のデュアル解を出力します。

## 例

REPLで呼び出すと、要約が自動的に印刷されます：

```julia
julia> solution_summary(model)
[...]
```

関数内から要約の印刷を強制するには `print` を使用します：

```julia
function foo(model)
    print(solution_summary(model))
    return
end
```
