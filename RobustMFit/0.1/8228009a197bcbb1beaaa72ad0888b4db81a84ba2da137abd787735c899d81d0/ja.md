```
Huber(kL::Real, kU::Real) <: HuberSetting
Huber(k::Real) <: HuberSetting
```

ハイパー関数の使用におけるM推定のための関数選択のデータ型。`kL`と`kU`はそれぞれ下限および上限の調整定数を与えます。調整定数が1つだけ提供された場合、対称関数が仮定されます。

# 例

```julia
Huber(1.5, 2)
Huber(1.5)
```
