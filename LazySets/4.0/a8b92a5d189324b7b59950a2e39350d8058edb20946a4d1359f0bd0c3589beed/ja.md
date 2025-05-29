# 拡張ヘルプ

```
isuniversal(S::LazySets.AbstractCentrallySymmetricPolytope, [witness]::Bool=false)
```

### アルゴリズム

ウィットネスは、方向 `d = [1, 0, …, 0]` におけるサポートベクトルを計算し、その上に `d` を加えることによって得られます。
