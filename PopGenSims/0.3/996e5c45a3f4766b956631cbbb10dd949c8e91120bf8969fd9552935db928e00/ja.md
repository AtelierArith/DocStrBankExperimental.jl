```
simulate(data::PopData; n::Int)
```

`PopData`オブジェクトから導出された各集団のアレル頻度を使用して、各集団あたり`n`人の個体をシミュレートします。`n` * `n_populations`サンプルを持つ新しい`PopData`オブジェクトを返します。

```
simulate(data::PopData; scale::Int)
```

`PopData`に現れる比率と同じ比率で各集団あたりの個体をシミュレートします。各集団のアレル頻度を使用します。シミュレーションのボリュームは`scale`を使用して倍増できます。つまり、同じ比率を維持しながらサンプル数を2倍にしたい場合、`scale`は`2`になります。`n_samples` * `scale`サンプルを持つ新しい`PopData`オブジェクトを返します。    

**例**

```julia
julia> cats = @nanycats;

julia> sims = simulate(cats, n = 100)
PopData{Diploid, 9 Microsatellite Loci}
  Samples: 1700
  Populations: 17
  
julia> sims_prop = simulate(cats, scale = 3)
  PopData{Diploid, 9 Microsatellite Loci}
    Samples: 711
    Populations: 17
```
