```julia
continuation(br, ind_bif, lens2; ...)
continuation(
    br,
    ind_bif,
    lens2,
    options_cont;
    prob,
    start_with_eigen,
    detect_codim2_bifurcation,
    update_minaug_every_step,
    kwargs...
)

```

コダイメンション2の連続性の折れ線/ホップ点。この関数は、折れ線/ホップ点の初期推測を、最小限に拡張された定式化に基づく折れ線/ホップ点の曲線に変換します。引数は次のとおりです。

  * `br` [continuation](@ref Library-Continuation)への呼び出し後に返される結果
  * `ind_bif` `br`内の分岐インデックス
  * `lens2` 連続性に使用される2番目のパラメータ、最初のものは`br`を計算するために使用されるものです。例: `getlens(br)`
  * `options_cont = br.contparams` 通常の[continuation](@ref Library-Continuation)に渡す引数

# オプション引数:

  * `linsolve_adjoint` (J+iω)˟ ⋅sol = rhs または Jᵗ ⋅sol = rhs のためのソルバー
  * `bdlinsolver` 制約方程式のための境界付き線形ソルバー
  * `bdlinsolver_adjoint` 制約方程式のための境界付き線形ソルバーで、左上ブロック (J-iω)˟ または Jᵗ。最小限に拡張された折れ線/ホップ関数の線形ソルバーで必要です。このオプションは、特定の前処理器を持つ専用の線形ソルバーを渡すために使用できます。
  * `update_minaug_every_step` 最小限の定式化でのベクトル `a, b` を `update_minaug_every_step` ステップごとに更新
  * `detect_codim2_bifurcation ∈ {0,1,2}` ボグダノフ-タケンス、バウティン、カスプを検出するかどうか。`1`の場合は不正確な検出が使用されます。`2`の場合は、分岐を特定するために二分法が使用されます。デフォルト値 = 2。
  * `start_with_eigen = false` 最小限に拡張された問題を固有要素からの情報で開始するかどうか。`start_with_eigen = false`の場合、次のようになります。

      * `a::Nothing` 折れ線（またはホップ）のための J (resp. J-iω) の零ベクトルの推定。何も渡されない場合は、ランダムベクトルが使用されます。`AbstractArray`に依存しない場合は、これを渡すべきです。
      * `b::Nothing` 折れ線（またはホップ）のための Jᵗ (resp. (J-iω)˟) の零ベクトルの推定。何も渡されない場合は、ランダムベクトルが使用されます。`AbstractArray`に依存しない場合は、これを渡すべきです。
  * `kwargs` 通常の[continuation](@ref Library-Continuation)に渡すキーワード引数

ここで、パラメータは上記の通りですが、分岐の検出が有効になっている`continuation`への呼び出しの結果からブランチ`br`を渡す必要があります。また、`index`は、洗練したい`br`内のホップ点のインデックスです。

!!! tip "ODE問題"
    ODE問題の場合、オプション`bdlinsolver = MatrixBLS()`を渡して、行列ベースの境界付き線形ソルバーを使用する方が効率的です。


!!! tip "start_with_eigen"
    オプション`start_with_eigen = true`を使用することをお勧めします。

