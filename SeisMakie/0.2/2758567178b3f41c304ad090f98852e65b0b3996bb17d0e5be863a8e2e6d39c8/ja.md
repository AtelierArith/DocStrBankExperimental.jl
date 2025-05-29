```
SeisPlotAmplitude(d,fmax,dy ; <keyword arguments>)
```

振幅-周波数2D地震データ `d` をプロットします。

# 引数

  * `d::Array{Real,2}`: プロットする2Dデータ。

# キーワード引数

  * `fig=nothing`: プロットする図。指定しない場合は、新しい図が作成されて返されます。
  * `ax=nothing`: プロットする軸。指定しない場合は、新しい軸が作成されて返されます。
  * `fmax=100`: 最大周波数。
  * `dy=0.004`: 時間サンプル間隔。
  * `normalize=false`: データを正規化するかどうか。
  * `color=:red`: プロットの色。
  * `label=""`: 凡例に含めるプロットラベル。

# 例

```julia
julia> d = SeisLinearEvents();
julia> f, ax = SeisPlotAmplitude(d,100,0.004);
```

著者: Firas Al Chalabi (2024)
