```
NoOpLayer()
```

名前が示すように、何もしませんが、レイヤーの美しい印刷を可能にします。渡された入力はそのまま返されます。

# 例

```jldoctest
julia> model = NoOpLayer()
NoOpLayer()

julia> rng = Random.default_rng();
       Random.seed!(rng, 0);
       ps, st = Lux.setup(rng, model);
       x = 1
1

julia> y, st_new = model(x, ps, st)
(1, NamedTuple())
```
