```
Dateifier(args=Dict())
   Dict(
    :ahead => 1,
    :size => 7,
    :stride => 1
   )
)
```

1次元の日付系列をMLトレーニング用のスライディングウィンドウ行列に変換します

例: 

```
dtr = Dateifier(Dict())
lower = DateTime(2017,1,1)
upper = DateTime(2018,1,31)
dat=lower:Dates.Day(1):upper |> collect
vals = rand(length(dat))
x=DataFrame(Date=dat,Value=vals)
fit!(dtr,x)
res = transform!(dtr,x)
```

実装: `'fit!`, `transform!`
