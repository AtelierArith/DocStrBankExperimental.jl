```
@def_states(site, symbols)
```

指定されたサイトのために与えられた状態を定義します

# 例

```
@def_states(Fermion(),
[
    ["Emp", "0"] => [1., 0.],
    "Occ" => [0., 1.],
])
```
