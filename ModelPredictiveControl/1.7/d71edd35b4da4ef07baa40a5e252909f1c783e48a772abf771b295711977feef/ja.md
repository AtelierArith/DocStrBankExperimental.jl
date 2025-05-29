```
NonLinMPC(model::SimModel; <keyword arguments>)
```

[`SimModel`](@ref) `model`に基づいて非線形予測制御器を構築します。

[`NonLinModel`](@ref)と[`LinModel`](@ref)の両方がサポートされています（詳細は拡張ヘルプを参照）。制御器は、各離散時間$k$において以下の目的関数を最小化します：

$$
\begin{aligned}
\min_{\mathbf{Z}, ϵ}\ &  \mathbf{(R̂_y - Ŷ)}' \mathbf{M}_{H_p} \mathbf{(R̂_y - Ŷ)}   
                       + \mathbf{(ΔU)}'      \mathbf{N}_{H_c} \mathbf{(ΔU)}        \\&
                       + \mathbf{(R̂_u - U)}' \mathbf{L}_{H_p} \mathbf{(R̂_u - U)} 
                       + C ϵ^2  
                       + E J_E(\mathbf{U_e}, \mathbf{Ŷ_e}, \mathbf{D̂_e}, \mathbf{p})
\end{aligned}
$$

制約は[`setconstraint!`](@ref)の範囲内であり、カスタム不等式制約は次のようになります：

$$
\mathbf{g_c}(\mathbf{U_e}, \mathbf{Ŷ_e}, \mathbf{D̂_e}, \mathbf{p}, ϵ) ≤ \mathbf{0}
$$

決定変数は$\mathbf{Z}$とスラック$ϵ$です。デフォルトでは、[`SingleShooting`](@ref)の転写方法が使用されるため、$\mathbf{Z=ΔU}$となります。経済関数$J_E$は、高い経済コストを持つ解にペナルティを課すことができます。すべての重みを0に設定し、$E$だけを残すと、純粋な経済モデル予測制御器（EMPC）が作成されます。実際、$J_E$は経済的解釈がなくてもカスタム目的として任意の非線形関数にすることができます。$J_E$と$\mathbf{g_c}$の引数には、操作された入力、予測された出力、測定された外乱が含まれ、$k$から$k+H_p$まで拡張されます（詳細は拡張ヘルプを参照）：

$$
    \mathbf{U_e} = \begin{bmatrix} \mathbf{U}      \\ \mathbf{u}(k+H_p-1)   \end{bmatrix}  , \quad
    \mathbf{Ŷ_e} = \begin{bmatrix} \mathbf{ŷ}(k)   \\ \mathbf{Ŷ}            \end{bmatrix}  , \quad
    \mathbf{D̂_e} = \begin{bmatrix} \mathbf{d}(k)   \\ \mathbf{D̂}            \end{bmatrix}
$$

引数$\mathbf{p}$は任意の型のカスタムパラメータオブジェクトですが、後で変更したい場合は可変のものを使用してください（例：ベクトル）。他の変数の定義については、[`LinMPC`](@ref)の拡張ヘルプを参照してください。

!!! tip
    必要ない場合は、$J_E$と$\mathbf{g_c}$関数の引数を`_`に置き換えてください（以下の`JE`のデフォルト値を参照）。


このメソッドはデフォルトの状態推定器を使用します：

  * `model`が[`LinModel`](@ref)の場合、デフォルト引数を持つ[`SteadyKalmanFilter`](@ref)；
  * それ以外の場合、デフォルト引数を持つ[`UnscentedKalmanFilter`](@ref)。

この制御器は、各時間ステップで最適化のためにメモリを割り当てます。

!!! warning
    `MethodError: no method matching Float64(::ForwardDiff.Dual)`のようなエラーが発生した場合は、拡張ヘルプを参照してください。


# 引数

  * `model::SimModel` : 制御器の予測と状態推定に使用されるモデル。
  * `Hp=nothing`: 予測ホライズン$H_p$、[`NonLinModel`](@ref)の場合は指定する必要があります。
  * `Hc=2` : 制御ホライズン$H_c$。
  * `Mwt=fill(1.0,model.ny)` : $\mathbf{M}$重み行列の主対角成分（ベクトル）。
  * `Nwt=fill(0.1,model.nu)` : $\mathbf{N}$重み行列の主対角成分（ベクトル）。
  * `Lwt=fill(0.0,model.nu)` : $\mathbf{L}$重み行列の主対角成分（ベクトル）。
  * `M_Hp=Diagonal(repeat(Mwt,Hp))` : 正半定値対称行列$\mathbf{M}_{H_p}$。
  * `N_Hc=Diagonal(repeat(Nwt,Hc))` : 正半定値対称行列$\mathbf{N}_{H_c}$。
  * `L_Hp=Diagonal(repeat(Lwt,Hp))` : 正半定値対称行列$\mathbf{L}_{H_p}$。
  * `Cwt=1e5` : スラック変数の重み$C$（スカラー）、ハード制約のみの場合は`Cwt=Inf`を使用。
  * `Ewt=0.0` : 経済コストの重み$E$（スカラー）。
  * `JE=(_,_,_,_)->0.0` : 経済的またはカスタムコスト関数$J_E(\mathbf{U_e}, \mathbf{Ŷ_e},  \mathbf{D̂_e}, \mathbf{p})$。
  * `gc=(_,_,_,_,_,_)->nothing`または`gc!` : カスタム不等式制約関数$\mathbf{g_c}(\mathbf{U_e}, \mathbf{Ŷ_e}, \mathbf{D̂_e}, \mathbf{p}, ϵ)$、変更可能または変更不可（詳細は拡張ヘルプを参照）。
  * `nc=0` : カスタム不等式制約の数。
  * `p=model.p` : $J_E$および$\mathbf{g_c}$関数のパラメータ$\mathbf{p}$（任意の型）。
  * `transcription=SingleShooting()` : 最適化のための[`TranscriptionMethod`](@ref)。
  * `optim=JuMP.Model(Ipopt.Optimizer)` : 予測制御器で使用される非線形最適化器、[`JuMP.Model`](@extref)オブジェクトとして提供されます（デフォルトは[`Ipopt`](https://github.com/jump-dev/Ipopt.jl)最適化器）。
  * `gradient=AutoForwardDiff()` : 目的関数の勾配のための`AbstractADType`バックエンド、[`DifferentiationInterface` doc](@extref DifferentiationInterface List)を参照。
  * `jacobian=default_jacobian(transcription)` : 非線形制約のヤコビアンのための`AbstractADType`バックエンド、オプションについては上記の`gradient`を参照（拡張ヘルプでデフォルト）。
  * 追加のキーワード引数は、[`UnscentedKalmanFilter`](@ref)コンストラクタ（または[`SteadyKalmanFilter`](@ref)、[`LinModel`](@ref)の場合）に渡されます。

# 例

```jldoctest
julia> model = NonLinModel((x,u,_,_)->0.5x+u, (x,_,_)->2x, 10.0, 1, 1, 1, solver=nothing);

julia> mpc = NonLinMPC(model, Hp=20, Hc=1, Cwt=1e6)
NonLinMPC controller with a sample time Ts = 10.0 s, Ipopt optimizer, UnscentedKalmanFilter estimator and:
 20 prediction steps Hp
  1 control steps Hc
  1 slack variable ϵ (control constraints)
  1 manipulated inputs u (0 integrating states)
  2 estimated states x̂
  1 measured outputs ym (1 integrating states)
  0 unmeasured outputs yu
  0 measured disturbances d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    [`LinModel`](@ref)に基づく`NonLinMPC`制御器は、`for`ループの代わりに行列代数を使用して予測を計算します。この機能は、特に制約処理の最適化を加速することができ、私の知る限り他のパッケージでは利用できません。

    経済コスト$J_E$とカスタム制約$\mathbf{g_c}$関数は、拡張ベクトル$\mathbf{U_e}$（`nu*Hp+nu`要素）、$\mathbf{Ŷ_e}$（`ny+ny*Hp`要素）および$\mathbf{D̂_e}$（`nd+nd*Hp`要素）を引数として受け取ります。これらはすべて、$k$から$k + H_p$までの値を含みます（含む）。カスタム制約は、スラック$ϵ$（スカラー）も受け取ります。これは、`Cwt=Inf`の場合は常にゼロです。

    より正確には、$\mathbf{U_e}$の最後の2つの時間ステップは等しくなるように強制されます。すなわち、$\mathbf{u}(k+H_p) = \mathbf{u}(k+H_p-1)$です。これは、$H_c ≤ H_p$が$\mathbf{Δu}(k+H_p) = \mathbf{0}$を意味するためです。ベクトル$\mathbf{ŷ}(k)$と$\mathbf{d}(k)$は、現在の状態推定器の出力と測定された外乱であり、それぞれ、$\mathbf{Ŷ}$と$\mathbf{D̂}$は、$k+1$から$k+H_p$までの予測です。もし`LHS`が不等式$\mathbf{g_c}(\mathbf{U_e}, \mathbf{Ŷ_e}, \mathbf{D̂_e}, \mathbf{p}, ϵ) ≤ \mathbf{0}$の左辺の結果を表す場合、関数`gc`は2つの方法で実装できます：

    1. **非変更関数**（アウトオブプレイス）：`gc(Ue, Ŷe, D̂e, p, ϵ) -> LHS`として定義します。この構文はシンプルで直感的ですが、より多くのメモリを割り当てます。
    2. **変更関数**（インプレイス）：`gc!(LHS, Ue, Ŷe, D̂e, p, ϵ) -> nothing`として定義します。この構文は割り当てを減らし、計算負担を軽減する可能性があります。

    キーワード引数`nc`は`LHS`の要素数であり、`gc!`は`gc`引数のエイリアスです（`gc`と`gc!`の両方が非変更および変更関数を受け入れます）。

    デフォルトでは、最適化は目的関数と制約の導関数を計算するために密な[`ForwardDiff`](@extref ForwardDiff)自動微分（AD）に依存しています。1つの例外：`transcription`が[`SingleShooting`](@ref)でない場合、`jacobian`引数はこの[スパースバックエンド](@extref DifferentiationInterface AutoSparse-object)にデフォルト設定されます：

    ```julia
    AutoSparse(
        AutoForwardDiff(); 
        sparsity_detector  = TracerSparsityDetector(), 
        coloring_algorithm = GreedyColoringAlgorithm()
    )
    ```

    最適化器は一般的にADのような正確な導関数から利益を得ます。ただし、[`NonLinModel`](@ref)の状態空間関数はこの機能と互換性がある必要があります。これらの関数を書く際の一般的な間違いについては、[`JuMP` documentation](@extref JuMP Common-mistakes-when-writing-a-user-defined-operator)を参照してください。

    `Cwt≠Inf`の場合、`Ipopt`の属性`nlp_scaling_max_gradient`は`10/Cwt`に設定されます（すでに設定されていない場合）。$ϵ$の小さな値をスケールするためです。


```
