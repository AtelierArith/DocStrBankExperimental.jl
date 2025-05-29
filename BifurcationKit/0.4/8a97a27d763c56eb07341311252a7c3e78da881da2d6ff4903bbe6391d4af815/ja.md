```julia
newton(probPO, orbitguess, options; kwargs...)

```

これは、有限差分と台形法に基づいて関数 G を計算するための Krylov-Newton ソルバーです。

# 引数:

  * `prob` 関数 G をエンコードする [`PeriodicOrbitTrapProblem`](@ref) 型の問題
  * `orbitguess` 周期軌道の推測で、`orbitguess[end]` は軌道の周期の推定値です。これはサイズ `N * M + 1` のベクトルである必要があり、ここで `M` は時間スライスの数、`N` は位相空間の次元です。これは `prob` の `N, M` の数と互換性がある必要があります。
  * `par` 関数に渡されるパラメータ
  * `options` 通常の `newton` メソッドと同じ

ヤコビアン（および線形アルゴリズム）の選択を指定します。`jacobian` は `[:FullLU, :FullSparseInplace, :Dense, :DenseAD, :BorderedLU, :BorderedSparseInplace, :FullMatrixFree, :BorderedMatrixFree, :FullMatrixFreeAD]` のいずれかに属する必要があります。これは、関数 G のヤコビアン `dG` を反転する方法を選択するために使用されます。

  * `jacobian = :FullLU` の場合、`dG` のスパース行列表現に基づくデフォルトの線形ソルバーを使用します。この行列は各ニュートン反復で組み立てられます。これがデフォルトのアルゴリズムです。
  * `jacobian = :FullSparseInplace` の場合、これは `:FullLU` と同じですが、スパース行列 `dG` がインプレースで更新されます。この方法は、はるかに少ないメモリを割り当てます。場合によっては、`：FullLU` を使用するよりも大幅に高速です。この方法は、ヤコビアンのスパースパターンが常に同じである場合にのみ使用できます。
  * `jacobian = :Dense` の場合、上記と同じですが、行列 `dG` は密です。また、インプレースで更新されます。このオプションは、小さな次元の ODE を研究するのに便利です。
  * `jacobian = :DenseAD` の場合、ForwardDiff を使用してヤコビアンを評価します。
  * `jacobian = :BorderedLU` の場合、線形ソルバーのボーダー形状を利用し、LU 分解を使用して `dG` を反転します。
  * `jacobian = :BorderedSparseInplace` の場合、これは `:BorderedLU` と同じですが、サイクリック行列 `dG` がインプレースで更新されます。この方法は、はるかに少ないメモリを割り当てます。場合によっては、`：BorderedLU` を使用するよりも大幅に高速です。この方法は、ヤコビアンのスパースパターンが常に同じである場合にのみ使用できます。
  * `jacobian = :FullMatrixFree` の場合、`dG` に対して行列フリーの線形ソルバーが使用されます。ここでは、`dG` のサイクリック形状のために前処理器が非常に必要になる可能性が高いことに注意してください。これは GMRES の収束特性に悪影響を与えます。
  * `jacobian = :BorderedMatrixFree` の場合、行列フリーの線形ソルバーが使用されますが、`Jc` のみ（ドキュメントを参照）です。これは、`options.linsolver` が `Jc` を反転するために使用されることを意味します。これらの2つの行列フリーオプションは、特定の前処理器を使用するためにヤコビアン `dG` の異なる部分を公開します。たとえば、`Jc` に対する ILU 前処理器は、`dG` の制約を削除し、収束を悪化させる可能性があります。もちろん、これらの最後の2つの方法では、前処理器が必要になる可能性が高いです。
  * `jacobian = :FullMatrixFreeAD` の場合、微分の評価マップは自動微分を使用して導出されます。したがって、前の2つのケースとは異なり、ユーザーは行列フリーの微分を渡す必要はありません。
