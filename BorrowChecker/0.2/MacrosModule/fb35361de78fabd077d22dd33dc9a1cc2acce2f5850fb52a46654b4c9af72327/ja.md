```
@own [:mut] x = value
@own [:mut] x, y, z = (value1, value2, value3)
@own [:mut] for var in iter
    # body
end
@own [:mut] x  # equivalent to @own [:mut] x = x
@own [:mut] (x, y)  # equivalent to @own [:mut] (x, y) = (x, y)
```

新しい所有変数を作成します。`:mut`が指定されている場合、値は可変になります。そうでない場合、値は不変になります。

`for`ループ内でも`@own`を使用して、各イテレーションのために所有値を作成することができます。
