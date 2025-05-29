```
VectorGradientFunction{E, FT, JT, F, J, I} <: AbstractVectorGradientFunction{E, FT, JT}
```

関数 $f:\mathcal M → ℝ^n$ をその最初の導関数を含めて、ヤコビアンの勾配のベクトルとして表現します。

したがって、これには勾配 ``\operatorname{grad} f_i(p) ∈ T_{p}\mathcal M` が含まれます。これらの勾配を関数と同じ方法でベクトルに入れると、[`ComponentVectorialType`](@ref) が得られます。

$$
\operatorname{grad} f(p) = \Bigl( \operatorname{grad} f_1(p), \operatorname{grad} f_2(p), …, \operatorname{grad} f_n(p) \Bigr)^\mathrm{T}
∈ (T_{p}\mathcal M)^n
$$

ここでの利点は、個々の成分を個別に評価できることです。

# フィールド

  * `value!!::F`:          コスト関数 $f$、異なる形式を取ることができます
  * `cost_type::`[`AbstractVectorialType`](@ref):     `f` のタイプのデータを示す/保存する
  * `jacobian!!::G`:     $f$ のヤコビアン
  * `jacobian_type::`[`AbstractVectorialType`](@ref): $J_f$ のタイプのデータを示す/保存する
  * `parameters`:    ベクトル $f$ が返すサイズの数 `n`。

# コンストラクタ

```
VectorGradientFunction(f, Jf, range_dimension;
    evaluation::AbstractEvaluationType=AllocatingEvaluation(),
    function_type::AbstractVectorialType=FunctionVectorialType(),
    jacobian_type::AbstractVectorialType=FunctionVectorialType(),
)
```

`f` とそのヤコビアン（勾配のベクトル） `Jf` の `VectorGradientFunction` を作成します。ここで `f` は次元 `range_dimension` のユークリッド空間にマッピングされます。それらのタイプはそれぞれ `function_type` と `jacobian_type` によって指定されます。ヤコビアンはさらに、`evaluation=` キーワードによって指定されたアロケーションバリアントまたはインプレースバリアントとして与えることができます。
