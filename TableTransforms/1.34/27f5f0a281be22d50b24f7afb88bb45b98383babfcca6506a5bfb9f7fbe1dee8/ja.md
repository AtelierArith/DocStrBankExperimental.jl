```
Functional(fun)
```

`fun`を要素ごとに適用する変換。

```
Functional(col₁ => fun₁, col₂ => fun₂, ..., colₙ => funₙ)
```

各`colᵢ`列に対応する`funᵢ`関数を適用します。

# 例

```julia
Functional(exp)
Functional(log)
Functional(1 => exp, 2 => log)
Functional(:a => exp, :b => log)
Functional("a" => exp, "b" => log)
```
