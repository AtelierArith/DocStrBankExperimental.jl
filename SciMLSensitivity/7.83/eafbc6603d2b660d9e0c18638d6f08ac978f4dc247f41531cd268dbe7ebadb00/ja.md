```
struct NILSS{CS,AD,FDT,RNG,nType,gType} <: AbstractShadowingSensitivityAlgorithm{CS,AD,FDT}
```

前方モードの連続[非侵入的最小二乗シャドウイング](https://arxiv.org/abs/1611.00880)手法の実装です。`NILSS`は、`ODEProblem`のパラメータに対する長時間平均量の感度を、計算を不安定な部分空間に制約することによって計算することを可能にします。`NILSS`は、接線ソルバーとして連続時間の`ForwardSensitivity`メソッドを使用します。 (均質および非均質の) 接線解の指数的な膨張を避けるために、軌道は十分に小さなセグメントに分割されるべきであり、接線解はインターフェースで再スケーリングされます。NILSSの計算コストとメモリコストは、不安定な（正の）リャプノフ指数の数に比例してスケールします（LSSメソッドのように状態の数ではなく）。`NILSS`は、各時間ステップでヤコビ行列を明示的に構築することを避けるため、一般的に大規模なシステムサイズに対して`ForwardLSS`よりも好まれるべきです。

## コンストラクタ

```julia
NILSS(nseg, nstep; nus = nothing,
    rng = Xorshifts.Xoroshiro128Plus(rand(UInt64)),
    chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = autodiff,
    g = nothing)
```

## 引数

  * `nseg`: アトラクタ上の全時間間隔のセグメント数。
  * `nstep`: 各セグメントのステップ数。

## キーワード引数

  * `nus`: 不安定部分空間の次元。デフォルトは`nothing`です。`nus`は状態次元（`length(u0)`）以下でなければなりません。デフォルトの選択では、`nus = length(u0) - 1`がコンパイル時に設定されます。
  * `rng`: (擬似)乱数生成器。均質な接線状態（`w`）の初期化に使用されます。デフォルトは`Xorshifts.Xoroshiro128Plus(rand(UInt64))`です。
  * `autodiff`: 内部感度アルゴリズム計算で自動微分を使用します。デフォルトは`true`です。
  * `chunk_size`: フルヤコビ行列が構築される場合の前方モード微分のチャンクサイズ（`autojacvec=false`および`autodiff=true`）。デフォルトは自動的なチャンクサイズの選択のために`0`です。
  * `autojacvec`: 特別なシーディングを用いて自動微分によるヤコビ行列-ベクトル積を計算します。
  * `diff_type`: フルヤコビ行列が必要な場合にFiniteDiff.jlによってヤコビ行列を構築するために使用されるメソッド（`autodiff=false`）。
  * `g`: 長時間平均目的の瞬時目的関数。

## SciMLProblemサポート

この`sensealg`は`ODEProblem`のみをサポートします。この`sensealg`はイベント（コールバック）をサポートしていません。この`sensealg`は、目的が長時間平均量でありエルゴード的であると仮定します。すなわち、システムの時間発展は、指定された初期条件に依存せず、無限の時間にわたって質的に同じ振る舞いをするため、パラメータに対する感度のみが関心の対象となります。

## 参考文献

Ni, A., Blonigan, P. J., Chater, M., Wang, Q., Zhang, Z., Sensitivity analy- sis on chaotic dynamical system by Non-Intrusive Least Square Shadowing (NI-LSS), in: 46th AIAA Fluid Dynamics Conference, AIAA AVIATION Forum (AIAA 2016-4399), American Institute of Aeronautics and Astronautics, 1–16 (2016).

Ni, A., and Wang, Q. Sensitivity analysis on chaotic dynamical systems by Non-Intrusive Least Squares Shadowing (NILSS). Journal of Computational Physics 347, 56-77 (2017).
