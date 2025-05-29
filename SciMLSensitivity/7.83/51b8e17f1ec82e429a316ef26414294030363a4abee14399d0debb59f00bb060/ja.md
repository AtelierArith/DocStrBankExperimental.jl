```julia
NILSAS{CS, AD, FDT, RNG, SENSE, gType} <: AbstractShadowingSensitivityAlgorithm{CS, AD, FDT}
```

隣接モードの連続[非侵入的隣接最小二乗シャドウイング](https://arxiv.org/abs/1801.08674)手法の実装です。`NILSAS`は、`ODEProblem`のパラメータに対する長時間平均量の感度を、計算を不安定な部分空間に制約することによって計算することを可能にします。`NILSAS`は、各セグメントでSciMLSensitivity.jlの連続隣接感度手法を使用して（均質および非均質の）隣接解を計算します。隣接解の指数的な膨張を避けるために、軌道は十分に小さなセグメントに分割されるべきであり、隣接解はインターフェースで再スケーリングされます。NILSASの計算コストとメモリコストは、不安定な隣接リャプノフ指数の数に比例してスケールします（LSS法の状態数ではなく）。`NILSAS`は、各時間ステップでヤコビアンの明示的な構築を避けるため、一般的に大規模システムサイズに対して`AdjointLSS`よりも好まれるべきです。`NILSAS`は、多くのパラメータに対して`NILSS`よりも有利です。なぜなら、NILSASは追加コストをほとんどかけずに複数のパラメータに対する勾配を計算するからです。

## コンストラクタ

```julia
NILSAS(nseg, nstep, M = nothing; rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    adjoint_sensealg = BacksolveAdjoint(autojacvec = ReverseDiffVJP()),
    chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    g = nothing)
```

## 引数

  * `nseg`: アトラクタ上の全時間間隔のセグメント数。
  * `nstep`: 各セグメントのステップ数。
  * `M`: 均質な隣接解の数。この数は（正の、隣接）リャプノフ指数の数以上でなければなりません。デフォルトは`nothing`です。

## キーワード引数

  * `rng`: （擬似）乱数生成器。均質な隣接状態（`w`）の終了条件を初期化するために使用されます。デフォルトは`Xorshifts.Xoroshiro128Plus(rand(UInt64))`です。
  * `adjoint_sensealg`: 各セグメントで均質および非均質の隣接解を計算するための連続隣接感度手法。デフォルトは`BacksolveAdjoint(autojacvec=ReverseDiffVJP())`です。

      * `autojacvec`: 特別なシーディングを用いた自動微分によってベクトル-ヤコビアン積（`J'*v`）を計算します。デフォルトは`true`です。選択肢の全セットは次の通りです：

          * `false`: ヤコビアンはFiniteDiff.jlを介して構築されます
          * `true`: ヤコビアンはForwardDiff.jlを介して構築されます
          * `TrackerVJP`: vjpのためにTracker.jlを使用します。
          * `ZygoteVJP`: vjpのためにZygote.jlを使用します。
          * `EnzymeVJP`: vjpのためにEnzyme.jlを使用します。
          * `ReverseDiffVJP(compile=false)`: vjpのためにReverseDiff.jlを使用します。`compile`はテープを事前コンパイルするかどうかのブール値で、`f`関数に分岐（`if`または`while`文）がない場合にのみ行うべきです。
  * `autodiff`: ヤコビアンを構築する必要がある場合にヤコビアンを構築するために自動微分を使用します。デフォルトは`true`です。
  * `chunk_size`: フルヤコビアンが構築される場合の前方モード微分のチャンクサイズ（`autojacvec=false`および`autodiff=true`）。デフォルトはチャンクサイズの自動選択のための`0`です。
  * `diff_type`: フルヤコビアンが必要な場合にFiniteDiff.jlによってヤコビアンを構築するために使用されるメソッド（`autodiff=false`）。
  * `g`: 長時間平均目的の瞬時目的関数。

## SciMLProblemサポート

この`sensealg`は`ODEProblem`のみをサポートします。この`sensealg`はイベント（コールバック）をサポートしていません。この`sensealg`は、目的が長時間平均量でありエルゴード的であると仮定します。すなわち、システムの時間発展は、指定された初期条件に依存せず、無限の時間にわたって質的に同じ振る舞いをするため、パラメータに対する感度のみが関心の対象となります。

## 参考文献

Ni, A., and Talnikar, C., Adjoint sensitivity analysis on chaotic dynamical systems by Non-Intrusive Least Squares Adjoint Shadowing (NILSAS). Journal of Computational Physics 395, 690-709 (2019).
