```
@test_expr <type> <ex>
```

構文タイプが同じ式 `ex` を生成するかどうかをテストします。対応する構文タイプのインスタンスを返します。このマクロを使用する前に `using Test` が必要です。

# 例

```julia
def = @test_expr JLFunction function (x, y)
    return 2
end
@test is_kw_fn(def) == false
```
