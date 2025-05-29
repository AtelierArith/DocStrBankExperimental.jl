```julia
coffset(FES::ExtendableFEMBase.FESpace) -> Int64

```

は、各コンポーネントの自由度間のオフセットを返します（すなわち、コンポーネントに影響を与えるスカラー自由度の数、ベクトル値の自由度は最後に格納されます）。
