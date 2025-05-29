```
VectorHessianFunction{E, FT, JT, HT, F, J, H, I} <: AbstractVectorGradientFunction{E, FT, JT}
```

関数 $f:\mathcal M M → ℝ^n$ を、その最初の導関数を含めて、勾配のベクトルまたはヤコビアンとして、そしてヘッセ行列を構成する成分関数のヘッセ行列のベクトルとして表現します。

ヤコビアンとヘッセ行列は、長さ `n` の冪多様体の単一の接空間または接空間のシーケンスのいずれかにマッピングできます。

# フィールド

  * `value!!::F`:          コスト関数 $f$、異なる形式を取ることができます
  * `cost_type::`[`AbstractVectorialType`](@ref):     `f` のタイプを示す / 文字列データ
  * `jacobian!!::G`:     $f$ のヤコビアン $J_f$
  * `jacobian_type::`[`AbstractVectorialType`](@ref): $J_f$ のタイプを示す / 保存するデータ
  * `hessians!!::H`:     $f$ のヘッセ行列（成分ごとの意味で）
  * `hessian_type::`[`AbstractVectorialType`](@ref):  $H_f$ のタイプを示す / 保存するデータ
  * `range_dimension`:    ベクトル $f$ が返すサイズの数 `n`。

# コンストラクタ

```
VectorHessianFunction(f, Jf, Hess_f, range_dimension;
    evaluation::AbstractEvaluationType=AllocatingEvaluation(),
    function_type::AbstractVectorialType=FunctionVectorialType(),
    jacobian_type::AbstractVectorialType=FunctionVectorialType(),
    hessian_type::AbstractVectorialType=FunctionVectorialType(),
)
```

`f` とそのヤコビアン（勾配のベクトル） `Jf` および（ベクトルの）ヘッセ行列の `VectorHessianFunction` を作成します。ここで、`f` は次元 `range_dimension` のユークリッド空間にマッピングされます。それらのタイプは、それぞれ `function_type`、`jacobian_type`、および `hessian_type` によって指定されます。ヤコビアンとヘッセ行列は、`evaluation=` キーワードによって指定されたアロケーションバリアントまたはインプレースバリアントとして与えることもできます。
