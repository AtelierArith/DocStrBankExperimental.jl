```
accumulation(rate, t)
accumulation(rate, from, to)
```

`rate`を時間`t`または区間`(from, to)`のために累積します。`rate`が`Rate`でない場合、それは1期間ごとに複利計算される`Periodic`レートであると見なされます。すなわち、`Periodic(rate,1)`です。

```
# 例
```

```julia-repl
julia> accumulation(0.03, 10)
1.3439163793441222

julia> accumulation(Periodic(0.03, 2), 10)
1.3468550065500535

julia> accumulation(Continuous(0.03), 10)
1.3498588075760032

julia> accumulation(0.03, 5, 10)
1.1592740743
```
