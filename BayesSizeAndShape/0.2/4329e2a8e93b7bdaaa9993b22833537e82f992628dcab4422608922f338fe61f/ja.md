```
SizeAndShapeWithReflectionMCMC(
    landmarks::Array{Float64,3}, 
    fm::FormulaTerm,
    covariates::DataFrame, 
    iterations::NamedTuple{(:iter, :burnin, :thin),Tuple{Int64,Int64,Int64}},
    betaprior::ContinuousUnivariateDistribution,
    sigmaprior::ContinuousMatrixDistribution
)
```

サイズと形状モデルの事後サンプル - このバージョンでは、反射情報を持つ二次元データのみが許可されています。  この関数は、`SizeAndShapeModelOutput`型のオブジェクトを返します。

# 引数

次のように定義します。

  * `n` はオブジェクトの数;
  * `k+1` は各オブジェクトの記録されたランドマークの数;
  * `p` は各ランドマークの次元（p=2またはp=3のみ）

関数の引数は次のとおりです。

  * `landmarks`: データを持つ三次元 `Array` で、次元は $(k+1)\times p \times n$ です;
  * `fm`: 左辺に1があり、右辺に実際の回帰式がある `formula` - 切片が必要です;
  * `covariates`: 共変量の `DataFrame`。式 `fm` は `DataFrame` の列名の中で共変量を探します;
  * `iterations`: MCMCアルゴリズムの `iter`、`burnin`、および `thin` の値を持つ `NamedTuple`;
  * `betaprior`: すべての回帰係数の事前分布として使用される `Normal` 分布;
  * `sigmaprior`: 共分散行列の事前分布として使用される `InverseWishart` 分布。
