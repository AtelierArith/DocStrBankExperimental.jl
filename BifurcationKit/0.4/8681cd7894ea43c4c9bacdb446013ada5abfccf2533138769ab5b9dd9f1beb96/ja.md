```julia
continuation(br, ind_bif; ...)
continuation(
    br,
    ind_bif,
    options_cont;
    alg,
    δp,
    ampfactor,
    use_normal_form,
    nev,
    usedeflation,
    verbosedeflation,
    max_iter_deflation,
    perturb,
    plot_solution,
    Teigvec,
    scaleζ,
    autodiff,
    tol_fold,
    kwargs_deflated_newton,
    kwargs...
)

```

分岐点での自動分岐切り替えは、正規形の計算に基づいています。詳細は[Branch switching](@ref Branch-switching-page)で提供されています。使用例は[2d generalized Bratu–Gelfand problem](@ref)に示されています。

# 引数

  * `br` [`continuation`](@ref)への呼び出しからの分岐結果
  * `ind_bif` 分岐元の`br`における分岐点のインデックス
  * `options_cont` [`continuation`](@ref)への呼び出しのオプション

# オプション引数

  * `alg = br.alg` 使用する継続アルゴリズム、デフォルト値: `br.alg`
  * `δp` 分岐したブランチのパラメータの特定の値を指定するために使用され、これは通常`options_cont.ds`によって決定されます。これにより、`options_cont.dsmax`よりも大きなステップを使用できます。
  * `ampfactor = 1` 分岐した解の振幅を変更するための係数。分岐したブランチが非常に急な場合に、分岐した解を拡大するのに便利です。また、ピッチフォーク分岐における上部/下部ブランチを選択するためにも使用できます。以下の`use_normal_form`も参照してください。
  * `use_normal_form = true`。`use_normal_form = true`の場合、正規形が計算され、その予測子が生成され、推測が自動的に形成されます。`use_normal_form = false`の場合、パラメータ値`p = p₀ + δp`と推測`x = x₀ + ampfactor .* e`（ここで`e`はカーネルのベクトル）を初期推測として使用します。これは、自動分岐切り替えが機能しない場合に便利です。
  * `nev` 正しい固有ベクトルを得るために計算される固有値の数
  * `usedeflation = false` 分岐した推測を見つけるのを助けるために非線形デフレーションを使用するかどうか（[Deflated problems](@ref Deflated-problems)を参照）
  * `verbosedeflation` デフレートニュートンの反復を印刷
  * `max_iter_deflation` デフレートニュートンにおけるニュートンステップの数
  * `perturb = identity` デフレートニュートン中に使用する摂動関数
  * `Teigvec = _getvectortype(br)` 固有ベクトルのタイプ。`br`がファイルから読み込まれ、この情報が失われた場合に便利です
  * `scaleζ = norm` 正規形計算中にベクトルを正規化するためのノルムを渡す
  * `plot_solution` 問題`br.prob`におけるプロット解法を変更
  * `kwargs` [`continuation`](@ref)へのオプション引数、通常の`continuation`と[`get_normal_form`](@ref)への引数

!!! tip "高度な使用"
    非常に大きなモデルと特別なハードウェア（GPU、クラスター）を使用する場合、縮小方程式、予測子、および分岐したブランチの計算を分離することをお勧めします。これらのバージョンを呼び出す方法については`methods(BifurcationKit.multicontinuation)`を参照してください。これらのメソッドは、非常に高いメモリ圧力のあるGPUでテストされています。

