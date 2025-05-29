```
approximationproblem(args...)
```

# 例

## 辞書からapproximationproblemを作成する

```jldocs
julia> approximationproblem(Fourier(10))
```

## 辞書とドメイン（extensionframe）からapproximationproblemを作成する

```jldocs
julia> approximationproblem(Fourier(10),0.0..0.5)
```

## プラットフォームからapproximationproblemを作成する

```jldocs
julia> approximationproblem(FourierPlatform())
```

## プラットフォームとプラットフォームパラメータからapproximationproblemを作成する

```jldocs
julia> approximationproblem(FourierPlatform(), 10)
```
