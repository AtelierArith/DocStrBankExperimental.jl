```
Matrifier(Dict(
   Dict(
    :ahead  => 1,
    :size   => 7,
    :stride => 1,
  )
)
```

1-D 時系列をスライディングウィンドウ行列に変換して ML トレーニングを行います：

  * `:ahead`  => 予測するステップ数
  * `:size`   => スライディングウィンドウのサイズ
  * `:stride` => スライディングウィンドウの重複量

例：

```
mtr = Matrifier(Dict(:ahead=>24,:size=>24,:stride=>5))
lower = DateTime(2017,1,1)
upper = DateTime(2017,1,5)
dat=lower:Dates.Hour(1):upper |> collect
vals = 1:length(dat)
x = DataFrame(Date=dat,Value=vals)
fit!(mtr,x)
res = transform!(mtr,x)
```

実装： `fit!`, `transform`
