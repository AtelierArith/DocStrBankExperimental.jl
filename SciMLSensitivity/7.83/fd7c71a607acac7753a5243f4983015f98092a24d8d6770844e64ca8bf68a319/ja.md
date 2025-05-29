```julia
SteadyStateAdjoint{CS, AD, FDT, VJP, LS} <: AbstractAdjointSensitivityAlgorithm{CS, AD, FDT}
```

非線形解の随伴微分の実装。暗黙の関数定理を使用して、$f(u,p) = 0$ の解の `p` に関する導関数を直接計算します。

## コンストラクタ

```julia
SteadyStateAdjoint(; chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = autodiff, linsolve = nothing)
```

## キーワード引数

  * `autodiff`: ヤコビアンを構築する必要がある場合に、自動微分を使用してヤコビアンを構築します。デフォルトは `true` です。
  * `chunk_size`: フルヤコビアンが構築される場合の前方モード微分のチャンクサイズ（`autojacvec=false` および `autodiff=true`）。デフォルトは自動的なチャンクサイズの選択のために `0` です。
  * `diff_type`: `autodiff=false` の場合にフルヤコビアンを構築するために FiniteDiff.jl が使用する方法。
  * `autojacvec`: 特別なシーディングを使用して自動微分によるベクトル-ヤコビアン積 (`J'*v`) を計算します。選択肢の全セットは次のとおりです：

      * `nothing`: 自動的に vjp を選択する自動アルゴリズムを使用します。これはデフォルトであり、ほとんどのユーザーに推奨されます。
      * `false`: ヤコビアンは FiniteDiff.jl によって構築されます。
      * `true`: ヤコビアンは ForwardDiff.jl によって構築されます。
      * `TrackerVJP`: vjp のために Tracker.jl を使用します。
      * `ZygoteVJP`: vjp のために Zygote.jl を使用します。
      * `EnzymeVJP`: vjp のために Enzyme.jl を使用します。
      * `ReverseDiffVJP(compile=false)`: vjp のために ReverseDiff.jl を使用します。`compile` はテープを事前コンパイルするかどうかのブール値で、`f` 関数に分岐（`if` または `while` 文）がない場合にのみ行うべきです。
  * `linsolve`: 随伴解に使用される線形ソルバー。デフォルトは `nothing` で、効率的なアルゴリズムを自動的に選択するポリアルゴリズムを使用します。
  * `linsolve_kwargs`: 線形ソルバーに渡されるキーワード引数。

vjp の選択肢に関する詳細については、感度アルゴリズムのドキュメントページまたは vjp タイプのドキュメント文字列を参照してください。

## 参考文献

Johnson, S. G., Notes on Adjoint Methods for 18.336, Online at http://math.mit.edu/stevenj/18.336/adjoint.pdf (2007)
