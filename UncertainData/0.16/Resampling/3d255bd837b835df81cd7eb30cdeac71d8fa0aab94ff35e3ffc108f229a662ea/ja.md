```
resample(x::AbstractUncertainValueDataset, resampling::ConstrainedValueResampling)
```

`x`を再サンプリングします。最初に不確実な値を提供する分布/母集団のサポートを制約し、その後、制限されたサポートからサンプルを引きます。

サンプリングは、`x`の要素間に順次依存関係がないと仮定して行われるため、値のコレクションにすでに存在する可能性のある依存関係を超えて、引き出しに依存関係が導入されることはありません。

## 例

```julia
# 一部の例データ 
N = 50
x_uncertain = [UncertainValue(Normal, x, rand(Uniform(0.1, 0.8))) for x in rand(N)]
y_uncertain = [UncertainValue(Normal, y, rand(Uniform(0.1, 0.8))) for y in rand(N)]
x = UncertainValueDataset(x_uncertain)
y = UncertainValueDataset(y_uncertain)

# 異なる制約で再サンプリング
resample(x, ConstrainedValueResampling(TruncateStd(1.5))
resample(y, ConstrainedValueResampling(TruncateStd(0.5))
resample(y, ConstrainedValueResampling(TruncateQuantiles(0.2, 0.8))
```
