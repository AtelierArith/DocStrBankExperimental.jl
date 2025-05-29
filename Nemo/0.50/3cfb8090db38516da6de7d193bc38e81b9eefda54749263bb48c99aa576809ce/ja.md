```
conj(a::CalciumFieldElem; form::Symbol=:default)
```

`a`の複素共役を返します。オプションの`form`引数は、表現を指定することを可能にします。`:shallow`形式では、簡単な簡約が不可能な場合、$\overline{a}$が新しい拡張数として導入されます。`:deep`形式では、複素共役が再帰的に行われます。
