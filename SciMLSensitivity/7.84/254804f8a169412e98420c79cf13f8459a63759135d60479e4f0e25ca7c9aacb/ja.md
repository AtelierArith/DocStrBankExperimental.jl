```julia
ForwardSensitivity{CS, AD, FDT} <: AbstractForwardSensitivityAlgorithm{CS, AD, FDT}
```

拡張ODEを解くことによって導関数を伝播させるための連続前方感度分析の実装です。逆モード自動微分環境内で（すなわちZygoteを介して）使用されると、`solve`呼び出しの前方微分が引き起こされます。

## コンストラクタ

```julia
ForwardSensitivity(;
    chunk_size = 0, autodiff = true,
    diff_type = Val{:central},
    autojacvec = autodiff,
    autojacmat = false)
```

## キーワード引数

  * `autodiff`: 内部感度アルゴリズム計算で自動微分を使用します。デフォルトは`true`です。
  * `chunk_size`: フルヤコビ行列が構築される場合の前方モード微分のチャンクサイズ（`autojacvec=false`かつ`autodiff=true`）。デフォルトはチャンクサイズの自動選択のために`0`です。
  * `autojacvec`: 特別なシーディングを用いて自動微分によるヤコビ行列-ベクトル積を計算します。
  * `diff_type`: フルヤコビ行列が必要な場合にFiniteDiff.jlによってヤコビ行列を構築するために使用されるメソッドです（`autodiff=false`）。

さらなる詳細：

  * `autodiff=true`かつ`autojacvec=true`の場合、ヤコビ行列を構築せずに積を計算するために、1チャンクの`J*v`前方モード方向導関数計算トリックが使用されます（ForwardDiff.jlを介して）。
  * `autodiff=false`かつ`autojacvec=true`の場合、ヤコビ行列を構築せずに`J*v`を計算するために数値的方向導関数トリック`(f(x+epsilon*v)-f(x))/epsilon`が使用されます。
  * `autodiff=true`かつ`autojacvec=false`の場合、ヤコビ行列はチャンク化された前方モード自動微分を介して構築されます（ForwardDiff.jlを介して）。
  * `autodiff=false`かつ`autojacvec=false`の場合、ヤコビ行列はFiniteDiff.jlを介して有限差分によって構築されます。

## SciMLProblemサポート

この`sensealg`はコールバック（イベント）なしの`ODEProblem`のみをサポートします。
