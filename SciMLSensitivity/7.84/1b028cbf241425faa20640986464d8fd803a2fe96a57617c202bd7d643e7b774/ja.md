```julia
ForwardLSS{CS, AD, FDT, RType, gType} <: AbstractShadowingSensitivityAlgorithm{CS, AD, FDT}
```

離散的前方モード[最小二乗シャドウイング](https://arxiv.org/abs/1204.0159) (LSS) メソッドの実装です。LSSは、カオス系の初期値問題（`ODEProblem`）の条件が悪い問題を、条件が良い最小二乗問題に置き換えます。これにより、`ODEProblem`のパラメータに対する長時間平均量の感度を計算することが可能になります。LSSの計算コストは（状態数 x 時間ステップ数）に比例します。軌道の時間 `T` に対して、`T^(-1/2)` の速度で正しい感度に収束します。より効率的な非侵入的定式化については、`NILSS()` および `NILSAS()` を参照してください。

## コンストラクタ

```julia
ForwardLSS(;
    chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    LSSregularizer = TimeDilation(10.0, 0.0, 0.0),
    g = nothing)
```

## キーワード引数

  * `autodiff`: ヤコビアンを構築する必要がある場合、自動微分を使用してヤコビアンを構築します。デフォルトは `true` です。
  * `chunk_size`: フルヤコビアンが構築される場合の前方モード微分のチャンクサイズ（`autojacvec=false` および `autodiff=true`）。デフォルトは自動的にチャンクサイズを選択するための `0` です。
  * `diff_type`: フルヤコビアンが必要な場合に、FiniteDiff.jlがヤコビアンを構築するために使用するメソッド（`autodiff=false`）。
  * `LSSregularizer`: `LSSregularizer`を使用することで、3つの異なる正則化ルーチンの中から選択できます。デフォルトの選択は `TimeDilation(10.0,0.0,0.0)` です。

      * `CosWindowing()`: 時間グリッドのコサインウィンドウ処理、すなわち、時間グリッド（保存された時間ステップ）がコサインを使用して変換されます。
      * `Cos2Windowing()`: 時間グリッドのコサイン二乗ウィンドウ処理。
      * `TimeDilation(alpha::Number,t0skip::Number,t1skip::Number)`: 時間の拡張に対応します。`alpha`は重みを制御します。`t0skip`と`t1skip`は、それぞれ軌道の開始時と終了時に切り捨てられる時間を示します。
  * `g`: 長時間平均目的の瞬時目的関数。

## SciMLProblem サポート

この`sensealg`は`ODEProblem`のみをサポートします。この`sensealg`はイベント（コールバック）をサポートしていません。この`sensealg`は、目的が長時間平均量であり、エルゴード的であると仮定します。すなわち、システムの時間発展は、指定された初期条件に依存せず、無限の時間にわたって質的に同じ振る舞いをするため、パラメータに対する感度のみが関心の対象となります。

## 参考文献

Wang, Q., Hu, R., and Blonigan, P. カオス限界サイクル振動の最小二乗シャドウイング感度分析. Journal of Computational Physics, 267, 210-224 (2014).

Wang, Q., エルゴード平均の導関数を計算するための最小二乗シャドウイング法の収束, SIAM Journal on Numerical Analysis, 52, 156–170 (2014).

Blonigan, P., Gomez, S., Wang, Q., 渦流体の感度分析のための最小二乗シャドウイング, in: 52nd Aerospace Sciences Meeting, 1–24 (2014).
