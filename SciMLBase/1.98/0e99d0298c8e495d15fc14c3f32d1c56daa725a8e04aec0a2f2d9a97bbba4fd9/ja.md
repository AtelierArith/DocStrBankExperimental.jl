```
OptimizationFunction{iip,AD,F,G,H,HV,C,CJ,CH,HP,CJP,CHP,S,S2,HCV,CJCV,CHCV} <: AbstractOptimizationFunction{iip,specialize}
```

目的関数 `f` の最適化の表現であり、次のように定義されます：

$$
\min_{u} f(u,p)
$$

およびその関連するすべての関数、例えば `f` の勾配、ヘッセ行列などです。すべてのケースにおいて、`u` は状態であり、`p` はパラメータです。

## コンストラクタ

```julia
OptimizationFunction{iip}(f, adtype::AbstractADType = NoAD();
                          grad = nothing, hess = nothing, hv = nothing,
                          cons = nothing, cons_j = nothing, cons_h = nothing,
                          lag_h = nothing,
                          hess_prototype = nothing, cons_jac_prototype = __has_jac_prototype(f) ? f.jac_prototype : nothing,
                          cons_hess_prototype = nothing,
                          lag_hess_prototype = nothing,
                          syms = __has_syms(f) ? f.syms : nothing,
                          paramsyms = __has_paramsyms(f) ? f.paramsyms : nothing,
                          observed = __has_observed(f) ? f.observed : DEFAULT_OBSERVED_NO_TIME,
                          hess_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          cons_jac_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          cons_hess_colorvec = __has_colorvec(f) ? f.colorvec : nothing,
                          lag_hess_colorvec = nothing,
                          sys = __has_sys(f) ? f.sys : nothing)
```

## 位置引数

  * `f(u,p)`: 最適化する関数。`u` は状態変数で、`p` は最適化のハイパーパラメータです。この関数はスカラーを返す必要があります。
  * `adtype`: "ADを介した最適化関数の定義" セクションを参照してください。

## キーワード引数

  * `grad(G,u,p)` または `G=grad(u,p)`: `u` に関する `f` の勾配
  * `hess(H,u,p)` または `H=hess(u,p)`: `u` に関する `f` のヘッセ行列
  * `hv(Hv,u,v,p)` または `Hv=hv(u,v,p)`: ヘッセ行列-ベクトル積 $(d^2 f / du^2) v$。
  * `cons(res,x,p)` または `cons(x,p)` : 制約関数で、最適化ルーチン内の変数の現在の値で評価された `i` 番目の制約の値を持つベクトルを変更または返す必要があります。この関数は単に関数評価を行い、等式または不等式の主張は、`lcons` および `ucons` として [`OptimizationProblem`](@ref) に渡された制約境界に基づいてソルバーによって適用されます。等式制約の場合、`lcons` と `ucons` は同じ値を渡す必要があります。
  * `cons_j(res,x,p)` または `res=cons_j(x,p)`: 制約のヤコビアン。
  * `cons_h(res,x,p)` または `res=cons_h(x,p)`: 制約のヘッセ行列で、`res[i]` が `cons` の `i` 番目の出力に関するヘッセ行列です。
  * `lag_h(res,x,sigma,mu,p)` または `res=lag_h(x,sigma,mu,p)`: ラグランジアンのヘッセ行列で、`sigma` はコスト関数の乗数で、`mu` は制約を掛けるラグランジュ乗数です。これは、ヘッセ行列の代わりに `hess` および `cons_h` に提供できます。
  * `paramjac(pJ,u,p)`: パラメータヤコビアン $df/dp$ を返します。
  * `hess_prototype`: ヘッセ行列に一致する型のプロトタイプ行列。例えば、ヘッセ行列が三対角行列である場合、適切なサイズの `Hessian` 行列をプロトタイプとして使用でき、積分器は可能な限りこの構造に特化します。非構造的なスパースパターンは、ヘッセ行列の正しいスパースパターンを持つ `SparseMatrixCSC` を使用する必要があります。デフォルトは `nothing` で、これは密なヘッセ行列を意味します。
  * `cons_jac_prototype`: 制約ヤコビアンに一致する型のプロトタイプ行列。デフォルトは `nothing` で、これは密な制約ヤコビアンを意味します。
  * `cons_hess_prototype`: 制約ヘッセ行列に一致する型のプロトタイプ行列。これは行列の配列として定義され、`hess[i]` が `i` 番目の出力に関するヘッセ行列です。例えば、ヘッセ行列がスパースである場合、`hess` は `Vector{SparseMatrixCSC}` です。デフォルトは `nothing` で、これは密な制約ヘッセ行列を意味します。
  * `syms`: 方程式の要素のシンボル名。これは `u0` のサイズと一致する必要があります。例えば、`u = [0.0,1.0]` で `syms = [:x, :y]` の場合、これは値に標準的な名前を適用し、解の中で `sol[:x]` を可能にし、プロット内の値に自動的に名前を付けます。
  * `paramsyms`: 方程式のパラメータのシンボル名。これは `p` のサイズと一致する必要があります。例えば、`p = [0.0, 1.0]` で `paramsyms = [:a, :b]` の場合、これは値に標準的な名前を適用し、解の中で `sol[:a]` を可能にします。
  * `hess_colorvec`: `hess_prototype` のスパースパターンに対する SparseDiffTools.jl 定義に従った色ベクトル。これは、有限差分および自動微分を使用してヘッセ行列の構築を特化させ、スパースパターンに基づいて加速された方法で計算されるようにします。デフォルトは `nothing` で、これは必要に応じて内部的に色ベクトルが計算されることを意味します。この操作のコストはスパースパターンに大きく依存します。
  * `cons_jac_colorvec`: `cons_jac_prototype` のスパースパターンに対する SparseDiffTools.jl 定義に従った色ベクトル。
  * `cons_hess_colorvec`: `cons_hess_prototype` のスパースパターンに対する SparseDiffTools.jl 定義に従った色ベクトルの配列。

## ADを介した最適化関数の定義

キーワード引数を使用することで、ユーザーはすべての可能な関数の定義を制御できますが、`OptimizationFunction` の生成を処理する最も簡単な方法は、ADタイプを指定することです。これにより、すべての追加関数が自動的に埋め込まれます。例えば、

```julia
OptimizationFunction(f,AutoZygote())
```

は、必要なすべての関数を定義するために [Zygote.jl](https://docs.sciml.ai/Zygote.jl/stable/) を使用します。直接定義された関数がある場合、自動AD定義はユーザーの選択を上書きしないことに注意してください。

ADベースの各コンストラクタは、それぞれのディスパッチを介して別々に文書化されています。

## iip: インプレース vs アウトオブプレース

この引数の詳細については、ODEFunction のドキュメントを参照してください。

## specialize: コンパイルと特化の制御

この引数の詳細については、ODEFunction のドキュメントを参照してください。

## フィールド

OptimizationFunction 型のフィールドは、入力の名前と直接一致します。
