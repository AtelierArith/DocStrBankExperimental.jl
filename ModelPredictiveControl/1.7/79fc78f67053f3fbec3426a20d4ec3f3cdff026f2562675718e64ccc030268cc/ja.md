```
MovingHorizonEstimator(model::SimModel; <keyword arguments>)
```

`model`（[`LinModel`](@ref) または [`NonLinModel`](@ref)）に基づいて移動ホライズン推定器（MHE）を構築します。

推定値に対する制約を処理できます。詳細は [`setconstraint!`](@ref) を参照してください。さらに、`model` は [`ExtendedKalmanFilter`](@ref) のように線形化されず、[`UnscentedKalmanFilter`](@ref) のように確率分布が近似されることもありません。ただし、各離散時間 $k$ で次の目的関数を最小化するため、計算コストは大幅に高くなります：

$$
\min_{\mathbf{x̂}_k(k-N_k+p), \mathbf{Ŵ}, ϵ}   \mathbf{x̄}' \mathbf{P̄}^{-1}       \mathbf{x̄} 
                                            + \mathbf{Ŵ}' \mathbf{Q̂}_{N_k}^{-1} \mathbf{Ŵ}  
                                            + \mathbf{V̂}' \mathbf{R̂}_{N_k}^{-1} \mathbf{V̂}
                                            + C ϵ^2
$$

ここで、到着コストは時間 $k-N_k$ で推定された状態から評価されます：

$$
\begin{aligned}
    \mathbf{x̄} &= \mathbf{x̂}_{k-N_k}(k-N_k+p) - \mathbf{x̂}_k(k-N_k+p) \\
    \mathbf{P̄} &= \mathbf{P̂}_{k-N_k}(k-N_k+p)
\end{aligned}
$$

共分散は $N_k$ 回繰り返されます：

$$
\begin{aligned}
    \mathbf{Q̂}_{N_k} &= \text{diag}\mathbf{(Q̂,Q̂,...,Q̂)}  \\
    \mathbf{R̂}_{N_k} &= \text{diag}\mathbf{(R̂,R̂,...,R̂)} 
\end{aligned}
$$

推定ホライズン $H_e$ はウィンドウの長さを制限します：

$$
N_k =                     \begin{cases}
    k + 1   &  k < H_e    \\
    H_e     &  k ≥ H_e    \end{cases}
$$

ベクトル $\mathbf{Ŵ}$ と $\mathbf{V̂}$ はそれぞれ、$j=N_k$ から $1$ までの推定されたプロセスノイズ $\mathbf{ŵ}(k-j+p)$ と、$j=N_k$ から $1$ までのセンサーノイズ $\mathbf{v̂}(k-j+1)$ を含みます。拡張ヘルプでは、これらの2つのベクトル、スラック変数 $ϵ$、および到着時の共分散の推定 $\mathbf{P̂}_{k-N_k}(k-N_k+p)$ を定義します。キーワード引数 `direct=true`（デフォルト値）の場合、上記の方程式では定数 $p=0$ となり、MHE は現在の形式になります。そうでない場合は $p=1$ となり、予測形式になります。

拡張プロセスモデルおよび $\mathbf{R̂}, \mathbf{Q̂}$ の共分散の詳細については、[`UnscentedKalmanFilter`](@ref) を参照してください。この推定器は、最適化のために各時間ステップでかなりの量のメモリを割り当てますが、現在は単一のシューティング転写としてハードコーディングされています。

!!! warning
    `MethodError: no method matching (::var"##")(::Vector{ForwardDiff.Dual})` のようなエラーが発生した場合は、拡張ヘルプを参照してください。


# 引数

!!! info
    *`強調`* されたキーワード引数は非Unicodeの代替です。


  * `model::SimModel` : （決定論的）推定のためのモデル。
  * `He=nothing` : 推定ホライズン $H_e$、指定する必要があります。
  * `i_ym=1:model.ny` : 測定された `model` の出力インデックス $\mathbf{y^m}$、残りは未測定の $\mathbf{y^u}$ です。
  * `σP_0=fill(1/model.nx,model.nx)` または *`sigmaP_0`* : 初期推定共分散 $\mathbf{P}(0)$ の主対角線、標準偏差ベクトルとして指定します。
  * `σQ=fill(1/model.nx,model.nx)` または *`sigmaQ`* : `model` のプロセスノイズ共分散 $\mathbf{Q}$ の主対角線、標準偏差ベクトルとして指定します。
  * `σR=fill(1,length(i_ym))` または *`sigmaR`* : 測定出力のセンサーノイズ共分散 $\mathbf{R}$ の主対角線、標準偏差ベクトルとして指定します。
  * `nint_u=0`: 操作入力の未測定の擾乱に対する確率モデルの積分器量（ベクトル）、積分器なしの場合は `nint_u=0` を使用します（拡張ヘルプを参照）。
  * `nint_ym=default_nint(model,i_ym,nint_u)` : 測定出力の未測定の擾乱に対する `nint_u` と同様ですが、積分器なしの場合は `nint_ym=0` を使用します（拡張ヘルプを参照）。
  * `σQint_u=fill(1,sum(nint_u))` または *`sigmaQint_u`* : 操作入力の未測定の擾乱に対する $\mathbf{Q_{int_u}}$（積分器で構成）に対して `σQ` と同様です。
  * `σPint_u_0=fill(1,sum(nint_u))` または *`sigmaPint_u_0`* : 操作入力の未測定の擾乱に対する $\mathbf{P_{int_u}}(0)$（積分器で構成）に対して `σP_0` と同様です。
  * `σQint_ym=fill(1,sum(nint_ym))` または *`sigmaQint_u`* : 測定出力の未測定の擾乱に対する $\mathbf{Q_{int_{ym}}}$（積分器で構成）に対して `σQ` と同様です。
  * `σPint_ym_0=fill(1,sum(nint_ym))` または *`sigmaPint_ym_0`* : 測定出力の未測定の擾乱に対する $\mathbf{P_{int_{ym}}}(0)$（積分器で構成）に対して `σP_0` と同様です。
  * `Cwt=Inf` : スラック変数の重み $C$、デフォルトは `Inf` で、ハード制約のみを意味します。
  * `optim=default_optim_mhe(model)` : （デフォルトは [`Ipopt`](https://github.com/jump-dev/Ipopt.jl) または [`OSQP`](https://osqp.org/docs/parsers/jump.html) で、`model` が [`LinModel`](@ref) の場合）最適化を解決するための二次または非線形最適化器を持つ [`JuMP.Model`](@extref) オブジェクト。
  * `gradient=AutoForwardDiff()` : `model` が [`LinModel`](@ref) でない場合の目的関数の勾配のための `AbstractADType` バックエンド。詳細は [`DifferentiationInterface` doc](@extref DifferentiationInterface List) を参照してください。
  * `jacobian=AutoForwardDiff()` : `model` が [`LinModel`](@ref) でない場合の制約のヤコビアンのための `AbstractADType` バックエンド。オプションについては上記の `gradient` を参照してください。
  * `direct=true`: $\mathbf{y^m}$ からの直接伝送で構築します（現在の推定器とも呼ばれ、遅延/予測形式とは対照的です）。

# 例

```jldoctest
julia> model = NonLinModel((x,u,_,_)->0.1x+u, (x,_,_)->2x, 10.0, 1, 1, 1, solver=nothing);

julia> estim = MovingHorizonEstimator(model, He=5, σR=[1], σP_0=[0.01])
MovingHorizonEstimator estimator with a sample time Ts = 10.0 s, Ipopt optimizer, NonLinModel and:
 5 estimation steps He
 0 slack variable ϵ (estimation constraints)
 1 manipulated inputs u (0 integrating states)
 2 estimated states x̂
 1 measured outputs ym (1 integrating states)
 0 unmeasured outputs yu
 0 measured disturbances d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    推定されたプロセスおよびセンサーノイズは次のように定義されます：

    $$
    \mathbf{Ŵ} = 
    \begin{bmatrix}
        \mathbf{ŵ}(k-N_k+p+0)     \\
        \mathbf{ŵ}(k-N_k+p+1)     \\
        \vdots                  \\
        \mathbf{ŵ}(k+p-1)
    \end{bmatrix} , \quad
    \mathbf{V̂} =
    \begin{bmatrix}
        \mathbf{v̂}(k-N_k+1)     \\
        \mathbf{v̂}(k-N_k+2)     \\
        \vdots                  \\
        \mathbf{v̂}(k)
    \end{bmatrix}
    $$

    拡張モデル関数 $\mathbf{f̂, ĥ^m}$ に基づいて：

    $$
    \begin{aligned}
        \mathbf{v̂}(k-j)     &= \mathbf{y^m}(k-j) - \mathbf{ĥ^m}\Big(\mathbf{x̂}_k(k-j), \mathbf{d}(k-j)\Big) \\
        \mathbf{x̂}_k(k-j+1) &= \mathbf{f̂}\Big(\mathbf{x̂}_k(k-j), \mathbf{u}(k-j), \mathbf{d}(k-j)\Big) + \mathbf{ŵ}(k-j)
    \end{aligned}
    $$

    定数 $p$ は `!direct` に等しい。言い換えれば、`direct==true` の場合、$\mathbf{Ŵ}$ と $\mathbf{V̂}$ は1つの時間ステップだけシフトされます。非デフォルトの予測形式で $p=1$ は、MHE にとって特に有用であり、MPC 最適化の後に高価な計算を移動させます。つまり、[`preparestate!`](@ref) はデフォルトで最適化を解決しますが、`direct=false` で [`updatestate!`](@ref) に延期することができます。

    [`SteadyKalmanFilter`](@ref) の拡張ヘルプでは、共分散の調整と `nint_ym` および `nint_u` 引数による拡張の詳細が説明されています。デフォルトの拡張スキームは同じであり、すなわち `nint_u=0` で、`nint_ym` は [`default_nint`](@ref) によって計算されます。コンストラクタは、結果として得られる拡張された [`NonLinModel`](@ref) の可観測性を検証しません。そのため、ユーザーはそれが依然として可観測であることを確認する責任があります。

    到着時の推定共分散 $\mathbf{P̂}_{k-N_k}(k-N_k+p)$ は、ウィンドウの開始時点 $k-N_k+p$ における状態推定の不確実性を示します。これは、現在の推定共分散 $\mathbf{P̂}_k(k)$ とは異なり、MHE によって計算されない値です（例えば、[`KalmanFilter`](@ref) とは対照的です）。3つのキーワード引数がその初期値を指定します：$\mathbf{P̂_i} =  \mathrm{diag}\{ \mathbf{P}(0), \mathbf{P_{int_{u}}}(0), \mathbf{P_{int_{ym}}}(0) \}$。初期状態推定 $\mathbf{x̂_i}$ は [`setstate!`](@ref) で手動で指定することも、[`LinModel`](@ref) のために [`initstate!`](@ref) で自動的に指定することもできます。$p=0$ の MHE は、ここにある他のすべての推定器とわずかに不一致です。これは、初期値を $\mathbf{x̂_i} = \mathbf{x̂}_{-1}(-1)$ および $\mathbf{P̂_i} = \mathbf{P̂}_{-1}(-1)$ と解釈し、最後の時間ステップからの *a posteriori* 推定です[^2]。$p=1$ の MHE は一貫性があり、これらを $\mathbf{x̂_i} = \mathbf{x̂}_{-1}(0)$ および $\mathbf{P̂_i} = \mathbf{P̂}_{-1}(0)$ と解釈します。

    [^2]: M. Hovd (2012), "A Note On The Smoothing Formulation Of Moving Horizon Estimation",   *Facta Universitatis*, Vol. 11 №2.

    最適化と到着共分散の更新は `model` に依存します：

      * `model` が [`LinModel`](@ref) の場合、最適化は時間変化するヘッセ行列を持つ二次計画として扱われ、一般的に非線形プログラミングよりも安価です。デフォルトでは、[`KalmanFilter`](@ref) が到着共分散を推定します（カスタマイズ可能）。
      * それ以外の場合、非線形プログラムが密な [`ForwardDiff`](@extref ForwardDiff) 自動微分（AD）を使用して目的関数と制約の導関数をデフォルトで計算します（カスタマイズ可能）。最適化器は一般的に AD のような正確な導関数から利益を得ます。ただし、`f` および `h` 関数はこの機能と互換性がある必要があります。これらの関数を書く際の一般的な間違いについては、[`JuMP` documentation](@extref JuMP Common-mistakes-when-writing-a-user-defined-operator) を参照してください。また、[`UnscentedKalmanFilter`](@ref) がデフォルトで到着共分散を推定します。

    スラック変数 $ϵ$ は、[`setconstraint!`](@ref) を参照して有効にすると制約を緩和します。デフォルトでは MHE では無効（`Cwt=Inf` から）ですが、2つ以上のタイプの境界がある問題に対しては有効にする必要があります（例えば、推定状態 $\mathbf{x̂}$ とセンサーノイズ $\mathbf{v̂}$ に対して）。`Cwt≠Inf` の場合、`Ipopt` の属性 `nlp_scaling_max_gradient` は `10/Cwt` に設定されます（すでに設定されていない場合）、$ϵ$ の小さい値をスケーリングします。到着共分散推定方法を指定するには、2番目のコンストラクタを使用してください。


```
