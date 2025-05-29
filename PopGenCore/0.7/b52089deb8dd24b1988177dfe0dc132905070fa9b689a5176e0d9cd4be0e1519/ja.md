```
filter(data::PopData, args...)
```

`PopData`が最初の引数で、フィルタリング条件が2番目の引数であるDataFrames.filter!の代替品です。`PopData`をその場で変更し、返します。**注意** 引数の順序はDataFrames.jlとは逆です。

**例**

```
x = @nancycats ;

filter!(x, :name => i -> i ∈ samplenames(x)[1:10]) ;

show(x)
PopData{Diploid, 9 Microsatellite loci}
  Samples: 10
  Populations: 1
```
