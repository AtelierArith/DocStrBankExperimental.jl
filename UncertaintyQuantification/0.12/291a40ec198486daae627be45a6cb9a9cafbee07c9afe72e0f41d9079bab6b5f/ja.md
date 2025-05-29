```
to_physical_space!(sr::SpectralRepresentation, df::DataFrame) -> Nothing
```

与えられた `DataFrame` 内のランダム位相角を標準正規分布から一様分布に変換します。

# 引数

  * `sr::SpectralRepresentation`: `SpectralRepresentation` 構造体のインスタンス。
  * `df::DataFrame`: 変換されるランダム位相角を含む `DataFrame`。

# 戻り値

何も返しません。`DataFrame` はその場で修正されます。

# 例

```julia
w = 0:0.1:10
psd = CloughPenzien(w, 1.0, 2.0, 0.05, 3.0, 0.1)
t = 0:0.1:10
name = :process1
sr = SpectralRepresentation(psd, t, name)
samples = sample(sr, 5)
to_standard_normal_space!(sr, samples)  # 標準正規空間に変換
to_physical_space!(sr, samples)         # 物理空間に戻す
```
