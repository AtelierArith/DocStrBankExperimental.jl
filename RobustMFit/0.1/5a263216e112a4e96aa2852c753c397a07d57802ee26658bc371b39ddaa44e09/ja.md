```
Andrew(kL::Real, kU::Real) <: AndrewSetting
Andrew(k::Real) <: AndrewSetting
```

アンドリューの波動関数を使用したM推定における関数選択のデータ型。`kL`と`kU`はそれぞれ下限および上限の調整定数を与えます。調整定数が1つだけ提供された場合、対称関数が仮定されます。

# 例

```julia
Andrew(4.5, 6)
Andrew(4.5)
```
