説明: これは、EMEPモデルの数式に基づいて湿性沈着を計算するために使用されるボックスモデルです。WetDepositionモデルを構築します。

# 例

```julia
@parameters t
wd = WetDeposition(t)
```
