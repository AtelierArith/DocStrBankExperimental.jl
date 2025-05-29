```julia
struct OptimizationFunction{iip, AD, F, G, FG, H, FGH, HV, C, CJ, CJV, CVJ, CH, HP, CJP, CHP, O, EX, CEX, SYS, LH, LHP, HCV, CJCV, CHCV, LHCV, ID} <: SciMLBase.AbstractOptimizationFunction{iip}
```

目的関数 `f` の表現で、次のように定義されます：

$$
\min_{u} f(u,p)
$$

およびその関連するすべての関数、例えば `f` の勾配、ヘッセ行列などです。すべてのケースにおいて、`u` は状態であり、この場合は最適化変数で、`p` は固定パラメータまたはデータです。

## コンストラクタ

```julia
OptimizationFunction{iip}(f, adtype::AbstractADType = NoAD();
                          grad = nothing, hess = nothing, hv = nothing,
                          cons = nothing, cons_j = nothing, cons_jvp = nothing,
                          cons_vjp = nothing, cons_h = nothing,
                          hess_prototype = nothing,
                          cons_jac_prototype = nothing,
                          cons_hess_prototype = nothing,
                          observed = __has_observed(f) ? f.observed : DEFAULT_OBSERVED_NO_TIME,
                          lag_h = nothing,
                          hess_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          cons_jac_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          cons_hess_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          lag_hess_colorvec = nothing,
                          sys = __has_sys(f) ? f.sys : nothing)
```

## 位置引数

  * `f(u,p)`: 最適化する関数。`u` は最適化変数で、`p` は目的に使用される固定パラメータまたはデータです。目的にそのようなパラメータが使用されていなくても、関数の引数として含める必要があります。ミニバッチ処理のために、`p` を使用してミニバッチを渡すことができます。やり方については、[こちら](https://docs.sciml.ai/Optimization/stable/tutorials/minibatch/)のチュートリアルを参照してください。これはスカラー、損失値を返す必要があります。
  * `adtype`: 以下のADを介した最適化関数の定義セクションを参照してください。

## キーワード引数

  * `grad(G,u,p)` または `G=grad(u,p)`: `u` に関する `f` の勾配。
  * `hess(H,u,p)` または `H=hess(u,p)`: `u` に関する `f` のヘッセ行列。
  * `hv(Hv,u,v,p)` または `Hv=hv(u,v,p)`: ヘッセ行列-ベクトル積 $(d^2 f / du^2) v$。
  * `cons(res,u,p)` または `res=cons(u,p)` : 制約関数で、渡された `res` 配列を現在の変数の値で評価した `i` 番目の制約の値で変更する必要があります。この関数は単に関数評価を行い、等式または不等式の主張は、`lcons` および `ucons` として [`OptimizationProblem`](@ref) に渡された制約境界に基づいてソルバーによって適用されます。等式制約の場合、`lcons` と `ucons` は同じ値を渡す必要があります。
  * `cons_j(J,u,p)` または `J=cons_j(u,p)`: 制約のヤコビ行列。
  * `cons_jvp(Jv,u,v,p)` または `Jv=cons_jvp(u,v,p)`: 制約のヤコビ行列-ベクトル積。
  * `cons_vjp(Jv,u,v,p)` または `Jv=cons_vjp(u,v,p)`: 制約のヤコビ行列-ベクトル積。
  * `cons_h(H,u,p)` または `H=cons_h(u,p)`: 制約のヘッセ行列で、`res[i]` が `cons` の `i` 番目の出力に関するヘッセ行列です。
  * `hess_prototype`: ヘッセ行列に一致する型のプロトタイプ行列。例えば、ヘッセ行列が三重対角行列の場合、適切なサイズの `Hessian` 行列をプロトタイプとして使用でき、最適化ソルバーは可能な限りこの構造に特化します。非構造的なスパースパターンは、ヘッセ行列の正しいスパースパターンを持つ `SparseMatrixCSC` を使用する必要があります。デフォルトは `nothing` で、これは密なヘッセ行列を意味します。
  * `cons_jac_prototype`: 制約ヤコビ行列に一致する型のプロトタイプ行列。デフォルトは `nothing` で、これは密な制約ヤコビ行列を意味します。
  * `cons_hess_prototype`: 制約ヘッセ行列に一致する型のプロトタイプ行列。これは行列の配列として定義され、`hess[i]` が `i` 番目の出力に関するヘッセ行列です。例えば、ヘッセ行列がスパースの場合、`hess` は `Vector{SparseMatrixCSC}` です。デフォルトは `nothing` で、これは密な制約ヘッセ行列を意味します。
  * `lag_h(res,u,sigma,mu,p)` または `res=lag_h(u,sigma,mu,p)`: ラグランジアンのヘッセ行列で、`sigma` はコスト関数の乗数で、`mu` は制約を乗算するラグランジュ乗数です。これは、ラグランジアンのヘッセ行列を直接使用するソルバーに対して `hess` および `cons_h` の代わりに提供できます。
  * `hess_colorvec`: `hess_prototype` のスパースパターンに従った色ベクトル。これは、有限差分および自動微分を使用してヘッセ行列の構築を特化させ、スパースパターンに基づいて加速された方法で計算されます。デフォルトは `nothing` で、これは必要に応じて内部で色ベクトルが計算されることを意味します。この操作のコストはスパースパターンに大きく依存します。
  * `cons_jac_colorvec`: `cons_jac_prototype` のスパースパターンに従った色ベクトル。
  * `cons_hess_colorvec`: `cons_hess_prototype` のスパースパターンに従った色ベクトルの配列。

[Symbolic Problem Building with ModelingToolkit](https://docs.sciml.ai/Optimization/stable/tutorials/symbolic/) インターフェースが使用される場合、次の引数も関連します：

  * `observed`: ユーザーにとって興味のある最適化変数の代数的組み合わせで、解の中で利用可能になります。これは単一または複数の式である可能性があります。
  * `sys`: `OptimizationSystem` を格納するフィールド。

## ADを介した最適化関数の定義

キーワード引数を使用することで、ユーザーはすべての可能な関数の定義を制御できますが、`OptimizationFunction` の生成を処理する最も簡単な方法は、ADTypes.jl からオプションを指定することで、ユーザーが自動的にすべての追加関数を埋め込むために使用する自動微分バックエンドを選択できるようにすることです。例えば、

```julia
OptimizationFunction(f,AutoForwardDiff())
```

は、[ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) を使用して必要なすべての関数を定義します。直接定義された関数がある場合、自動AD定義はユーザーの選択を上書きしないことに注意してください。

ADベースの各コンストラクタは、以下の [Automatic Differentiation Construction Choice Recommendations](@ref ad) セクションでそれぞれのディスパッチを介して別々に文書化されています。

## iip: インプレース vs アウトオブプレース

この引数の詳細については、ODEFunction のドキュメントを参照してください。

## specialize: コンパイルと特化の制御

この引数の詳細については、ODEFunction のドキュメントを参照してください。

## フィールド

OptimizationFunction 型のフィールドは、入力の名前と直接一致します。
