```
sample(sr::SpectralRepresentation, n::Integer=1) -> DataFrame
```

指定された `SpectralRepresentation` インスタンスのランダム位相角のサンプルを生成します。

# 引数

  * `sr::SpectralRepresentation`: `SpectralRepresentation` 構造体のインスタンス。
  * `n::Integer=1`: 生成するサンプルの数（デフォルトは1）。

# 戻り値

生成されたランダム位相角のサンプルを含む `DataFrame`。

# 例

```julia
w = 0:0.1:10
psd = CloughPenzien(w, 1.0, 2.0, 0.05, 3.0, 0.1)
t = 0:0.1:10
name = :process1
sr = SpectralRepresentation(psd, t, name)
samples = sample(sr, 5)
```
