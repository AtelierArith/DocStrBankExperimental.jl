```
StandardScaler(
   Dict( 
      :impl_args => Dict(
          :center => true,
          :scale => true
      )
   )
)
```

各特徴を (X - 平均) / 標準偏差 を使用して標準化します。標準偏差がゼロの場合は NaN を生成します。
