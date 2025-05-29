```
VectorHessianFunction{E, FT, JT, HT, F, J, H, I} <: AbstractVectorGradientFunction{E, FT, JT}
```

関数 $f:\mathcal M → ℝ^n$ を、その最初の導関数を含めて、勾配のベクトルまたはヤコビ行列として、そしてヘッセ行列を構成関数のヘッセ行列のベクトルとして表現します。

ヤコビ行列とヘッセ行列は、いずれも接空間のシーケンスまたは長さ `n` の冪多様体の単一の接空間にマッピングできます。

# フィールド

  * `value!!`:          コスト関数 $f$、異なる形式を取ることができます
  * `cost_type`:     `f` のタイプのための指示/文字列データ
  * `jacobian!!`:     $f$ のヤコビ行列
  * `jacobian_type`: $J_f$ のタイプのための指示/保存データ
  * `hessians!!`:     $f$ のヘッセ行列（成分ごとの意味で）
  * `hessian_type`:  $H_f$ のタイプのための指示/保存データ
  * `parameters`:    ベクトル $f$ が返すサイズの数 `n`。

# コンストラクタ

```
VectorGradientFunction(f, Jf, Hess_f, range_dimension;
    evaluation::AbstractEvaluationType=AllocatingEvaluation(),
    function_type::AbstractVectorialType=FunctionVectorialType(),
    jacobian_type::AbstractVectorialType=FunctionVectorialType(),
    hessian_type::AbstractVectorialType=FunctionVectorialType(),
)
```

`f` とそのヤコビ行列（勾配のベクトル） `Jf` および（ベクトルの）ヘッセ行列の `VectorGradientFunction` を作成します。ここで、`f` は次元 `range_dimension` のユークリッド空間にマッピングされます。それらのタイプはそれぞれ `function_type`、`jacobian_type`、および `hessian_type` によって指定されます。ヤコビ行列とヘッセ行列は、`evaluation=` キーワードによって指定されたアロケーティングバリアントまたはインプレースバリアントとして与えることもできます。
