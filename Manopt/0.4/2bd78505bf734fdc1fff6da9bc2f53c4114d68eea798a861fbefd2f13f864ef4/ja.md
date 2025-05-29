```
VectorGradientFunction{E, FT, JT, F, J, I} <: AbstractVectorGradientFunction{E, FT, JT}
```

関数 $f:\mathcal M → ℝ^n$ をその最初の導関数を含めて、ヤコビアンの勾配のベクトルとして表現します。

したがって、勾配 $\oepratorname{grad} f_i(p) ∈ T_p\mathcal M$ を持ちます。これらの勾配を関数と同じ方法でベクトルに入れると、[`ComponentVectorialType`](@ref) になります。

$$
\operatorname{grad} f(p) = \Bigl( \operatorname{grad} f_1(p), \operatorname{grad} f_2(p), …, \operatorname{grad} f_n(p) \Bigr)^{\mathrm{T}}
∈ (T_p\mathcal M)^n
$$

ここでの利点は、再び各コンポーネントを個別に評価できることです。

# フィールド

  * `value!!`:          コスト関数 $f$、異なる形式を取ることができます
  * `cost_type`:     `f` のタイプに関する指示 / 文字列データ
  * `jacobian!!`:     $f$ のヤコビアン
  * `jacobian_type`: $J_f$ のタイプに関する指示 / データの保存
  * `parameters`:    ベクトル $f$ が返すサイズの数 $n$。

# コンストラクタ

```
VectorGradientFunction(f, Jf, range_dimension;
    evaluation::AbstractEvaluationType=AllocatingEvaluation(),
    function_type::AbstractVectorialType=FunctionVectorialType(),
    jacobian_type::AbstractVectorialType=FunctionVectorialType(),
)
```

`f` とそのヤコビアン（勾配のベクトル） `Jf` の `VectorGradientFunction` を作成します。ここで `f` は次元 `range_dimension` のユークリッド空間にマッピングされます。それらのタイプはそれぞれ `function_type` と `jacobian_type` によって指定されます。ヤコビアンはさらに、`evaluation=` キーワードによって指定されたアロケーションバリアントまたはインプレースバリアントとして与えることができます。
