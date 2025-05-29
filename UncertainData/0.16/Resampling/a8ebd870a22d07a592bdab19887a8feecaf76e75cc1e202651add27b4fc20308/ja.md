```
resample(x::AbstractUncertainIndexValueDataset, resampling::SequentialInterpolatedResampling)
```

`x`を逐次的な再サンプリング制約に従って再サンプリングし、指定されたグリッドに対して描画を補間します。

この再サンプリングの方法は、`x`の要素間にいくつかの系列依存性を導入します - データセットにすでに存在するかもしれないものを*超えて*。これは、データセットの`i`-th値に逐次的な制約（例：`StrictlyIncreasing`）を課すことが、`i+1`th値からサンプリングする際に可能なことに制約を課すためです。

## 例

```julia
# 一部の例データ 
N = 50
x_uncertain = [UncertainValue(Normal, x, rand(Uniform(0.1, 0.8))) for x in rand(N)]
y_uncertain = [UncertainValue(Normal, y, rand(Uniform(0.1, 0.8))) for y in rand(N)]
x = UncertainValueDataset(x_uncertain)
y = UncertainValueDataset(y_uncertain)

time_uncertain = [UncertainValue(Normal, i, 1) for i = 1:length(x)];
time_certain = [CertainValue(i) for i = 1:length(x)];
timeinds_x = UncertainIndexDataset(time_uncertain)
timeinds_y = UncertainIndexDataset(time_certain)

X = UncertainIndexValueDataset(timeinds_x, x)
Y = UncertainIndexValueDataset(timeinds_y, y);

# 再サンプリング 
seqintp_resampling = SequentialInterpolatedResampling(StrictlyIncreasing(), RegularGrid(0:2:N))
resample(X, seqintp_resampling)
```
