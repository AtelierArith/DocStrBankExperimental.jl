```
dimensions(sr::SpectralRepresentation) -> Int
```

指定された `SpectralRepresentation` インスタンスの次元数（周波数）を返します。

# 引数

  * `sr::SpectralRepresentation`: `SpectralRepresentation` 構造体のインスタンス。

# 戻り値

次元数（周波数）を表す整数。

# 例

```julia
w = 0:0.1:10
psd = CloughPenzien(w, 1.0, 2.0, 0.05, 3.0, 0.1)
t = 0:0.1:10
name = :process1
sr = SpectralRepresentation(psd, t, name)
num_dimensions = dimensions(sr)
```
