```
parse(::FixedPoint, s)
```

この関数は文字列を解析し、それからFixedPoint型を作成しようとします。小数点の右側の桁数から精度を決定しようとします。

# 例

```
x = parse(FixedPoint, "41.25")
println(x)
41.25
println(x * 2)
82.50 
```
