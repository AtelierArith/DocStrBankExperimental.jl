```
resample(x::AbstractUncertainIndexValueDataset, resampling::ConstrainedIndexValueResampling)
```

`x`を再サンプリングします。最初に不確実なインデックスと値を提供する分布/母集団のサポートを制約し、その後、制限されたサポートからサンプルを引きます。

サンプリングは、`x`の要素間に順次依存関係がないと仮定して行われるため、値のコレクションにすでに存在する可能性のある依存関係を超えて、引き出しに依存関係が導入されることはありません。

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

###########################
# 再サンプリングスキームの定義 
###########################

# xの各インデックスを平均の周りの標準偏差の0.8倍で切り捨てる
constraints_x_inds = TruncateStd(0.8)

# yの各インデックスを平均の周りの標準偏差の1.5倍で切り捨てる
constraints_y_inds = TruncateStd(1.5)

# xの各値を20パーセンタイル範囲で切り捨てる
constraints_x_vals = [TruncateQuantiles(0.4, 0.6) for i = 1:N];

# yの各値を80パーセンタイル範囲で切り捨てる
constraints_y_vals = [TruncateQuantiles(0.1, 0.9) for i = 1:N];

cs_x = (constraints_x_inds, constraints_x_vals)
cs_y = (constraints_y_inds, constraints_y_vals)

###########
# 再サンプリング 
###########
resample(X, ConstrainedIndexValueResampling(cs_x))
resample(Y, ConstrainedIndexValueResampling(cs_y))
```
