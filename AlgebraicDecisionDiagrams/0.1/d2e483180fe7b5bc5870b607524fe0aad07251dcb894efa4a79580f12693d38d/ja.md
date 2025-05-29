```
MultilinearExpression
```

モノイドの辞書を係数として持つ多項式式データ型を実装します。

### 例

```julia

# 定数式を作成します

@show c = MultilinearExpression(7.4)

# 単一項を持つ式を作成します

@show e1 = MultilinearExpression(4.0,1) @show e2 = MultilinearExpression(3.0,1,3) ````
