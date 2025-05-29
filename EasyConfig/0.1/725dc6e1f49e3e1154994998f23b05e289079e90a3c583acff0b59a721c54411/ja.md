```
@config expr
```

NamedTupleのような構文またはブロック構文を使用して`Config`を作成します。以下の例は同等の`Config`を作成します：

```
@config (x.one=1, x.two=2, z=3)

@config x.one=1 x.two=2 z=3

@config begin
    x.one = 1
    x.two = 2
    z = 3
end

let
    c = Config()
    c.x.one = 1
    c.x.two = 2
    c.z = 3
end
```
