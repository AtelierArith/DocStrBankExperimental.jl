```julia
newton_hopf(
    prob,
    hopfpointguess,
    par,
    eigenvec,
    eigenvec_ad,
    options;
    normN,
    bdlinsolver,
    usehessian,
    kwargs...
)

```

この関数は、ホップ点の初期推定を、最小限に拡張された定式化に基づいてホップ問題の解に変換します。引数は次のとおりです。

  * `prob::AbstractBifurcationProblem` ここで `p` はパラメータのセットです。
  * `hopfpointguess` ホップ点の初期推定 (x*0, p*0)。これは、関数 `HopfPoint` によって返される `BorderedArray` である必要があります。
  * `par` ベクトル場に使用されるパラメータ
  * `eigenvec` iω 固有ベクトルの推定
  * `eigenvec_ad` -iω 固有ベクトルの推定
  * `options::NewtonPar` ニュートン-クリロフアルゴリズムのオプション、[`NewtonPar`](@ref)を参照してください。

# オプション引数:

  * `normN = norm`
  * `bdlinsolver` 制約方程式のための境界付き線形ソルバー
  * `kwargs` 通常のニュートン-クリロフソルバーに渡されるキーワード引数

# 簡略化された呼び出し:

ホップ点の初期推定を洗練させるための簡略化された呼び出し。より正確には、呼び出しは次のようになります。

```
newton_hopf(br::AbstractBranchResult, ind_hopf::Int; normN = norm, options = br.contparams.newton_options, kwargs...)
```

パラメータ/オプションは通常通りですが、分岐の検出が有効な `continuation` の呼び出しの結果から分岐 `br` を渡す必要があります。また、`index` は、洗練させたい `br` 内の分岐点のインデックスです。`options` 引数を使用して、`br` に保存されているものとは異なるニュートンパラメータを渡すことができます。

!!! tip "ヤコビ行列の転置"
    ヤコビ行列 `J` の随伴は、`Jᵗ = nothing` のときに内部で計算され、`transpose(J)` を使用します。これは、`J` が `AbstractArray` の場合にうまく機能します。この場合、`Jᵗ = (x, p) -> transpose(d_xF(x, p))` のようにヤコビ行列の随伴を渡さないでください。そうしないと、ヤコビ行列が二重に計算されます！


!!! tip "ODE問題"
    ODE問題の場合、オプション `bdlinsolver = MatrixBLS()` を渡すことで、行列ベースの境界付き線形ソルバーを使用する方が効率的です。

