```
add_obj_term!(data, model, ::Term, s::Symbol; oper)
```

`model`の目的関数にコスト/収益`s`を演算子`oper`に基づいて加算または減算します。コスト/収益はデータの目的変数リストに追加されます。
