```
UnscentedKalmanFilter(model::SimModel; <キーワード引数>)
```

[`SimModel`](@ref) `model`を用いて、無香料カルマンフィルタを構築します。

[`LinModel`](@ref)と[`NonLinModel`](@ref)の両方がサポートされています。無香料カルマンフィルタは、プロセスモデルに基づいています：

$$
\begin{aligned}
    \mathbf{x}(k+1) &= \mathbf{f̂}\Big(\mathbf{x}(k), \mathbf{u}(k), \mathbf{d}(k)\Big) 
                        + \mathbf{w}(k)                                                   \\
    \mathbf{y^m}(k) &= \mathbf{ĥ^m}\Big(\mathbf{x}(k), \mathbf{d}(k)\Big) + \mathbf{v}(k) \\
    \mathbf{y^u}(k) &= \mathbf{ĥ^u}\Big(\mathbf{x}(k), \mathbf{d}(k)\Big)                 \\
\end{aligned}
$$

ノイズ$\mathbf{v}(k), \mathbf{w}(k)$および共分散$\mathbf{R̂}, \mathbf{Q̂}$の詳細については、[`SteadyKalmanFilter`](@ref)を参照してください。2つの行列は、$\mathbf{Q̂ = \text{diag}(Q, Q_{int_u}, Q_{int_{ym}})}$および$\mathbf{R̂ = R}$から構成されます。関数$\mathbf{f̂, ĥ}$は、測定されていない外乱の確率モデルで拡張された`model`の状態空間関数です。これは、積分器の数`nint_u`および`nint_ym`によって指定されます（詳細は拡張ヘルプを参照）。モデルパラメータ$\mathbf{p}$は、簡潔さのために$\mathbf{f̂, ĥ}$関数の引数ではありません。$\mathbf{ĥ^m}$関数は、$\mathbf{ĥ}$関数の測定出力（および$\mathbf{ĥ^u}$の未測定出力）を表します。行列$\mathbf{P̂}$は、確率的なものと拡張された`model`状態の推定誤差共分散です。3つのキーワード引数は、$\mathbf{P̂}_{-1}(0) =  \mathrm{diag}\{ \mathbf{P}(0), \mathbf{P_{int_{u}}}(0), \mathbf{P_{int_{ym}}}(0) \}$でその初期値を指定します。初期状態推定$\mathbf{x̂}_{-1}(0)$は、[`setstate!`](@ref)を使用して手動で指定できます。この推定器は、`model`のシミュレーションがメモリを割り当てない場合、割り当てなしで動作します。

# 引数

!!! info
    *`強調`*されたキーワード引数は、非Unicodeの代替です。


  * `model::SimModel` : （決定論的）推定のためのモデル。
  * `i_ym=1:model.ny` : 測定された$\mathbf{y^m}$の`model`出力インデックス、残りは未測定の$\mathbf{y^u}$。
  * `σP_0=fill(1/model.nx,model.nx)`または*`sigmaP_0`* : 初期推定共分散$\mathbf{P}(0)$の主対角線を、標準偏差ベクトルとして指定。
  * `σQ=fill(1/model.nx,model.nx)`または*`sigmaQ`* : `model`のプロセスノイズ共分散$\mathbf{Q}$の主対角線を、標準偏差ベクトルとして指定。
  * `σR=fill(1,length(i_ym))`または*`sigmaR`* : `model`の測定出力のセンサーノイズ共分散$\mathbf{R}$の主対角線を、標準偏差ベクトルとして指定。
  * `nint_u=0`: 操作された入力の未測定外乱の確率モデルのための積分器の数量（ベクトル）、積分器なしの場合は`nint_u=0`を使用（詳細は拡張ヘルプを参照）。
  * `nint_ym=default_nint(model,i_ym,nint_u)` : 測定出力の未測定外乱のための`nint_u`と同じ、積分器なしの場合は`nint_ym=0`を使用（詳細は拡張ヘルプを参照）。
  * `σQint_u=fill(1,sum(nint_u))`または*`sigmaQint_u`* : 操作された入力の未測定外乱のための$\mathbf{Q_{int_u}}$（積分器で構成）。
  * `σPint_u_0=fill(1,sum(nint_u))`または*`sigmaPint_u_0`* : 操作された入力の未測定外乱のための$\mathbf{P_{int_u}}(0)$（積分器で構成）。
  * `σQint_ym=fill(1,sum(nint_ym))`または*`sigmaQint_u`* : 測定出力の未測定外乱のための$\mathbf{Q_{int_{ym}}}$（積分器で構成）。
  * `σPint_ym_0=fill(1,sum(nint_ym))`または*`sigmaPint_ym_0`* : 測定出力の未測定外乱のための$\mathbf{P_{int_{ym}}}(0)$（積分器で構成）。
  * `α=1e-3`または*`alpha`* : アルファパラメータ、状態分布の広がり$(0 < α ≤ 1)$。
  * `β=2`または*`beta`* : ベータパラメータ、状態分布の歪みと尖度$(β ≥ 0)$。
  * `κ=0`または*`kappa`* : カッパパラメータ、別の広がりパラメータ$(0 ≤ κ ≤ 3)$。
  * `direct=true`: $\mathbf{y^m}$からの直接伝送で構築（遅延/予測形式に対する現在の推定器）。

# 例

```jldoctest
julia> model = NonLinModel((x,u,_,_)->0.1x+u, (x,_,_)->2x, 10.0, 1, 1, 1, solver=nothing);

julia> estim = UnscentedKalmanFilter(model, σR=[1], nint_ym=[2], σPint_ym_0=[1, 1])
UnscentedKalmanFilter推定器、サンプル時間Ts = 10.0 s、NonLinModelおよび：
 1 操作された入力u（0の積分状態）
 3 推定された状態x̂
 1 測定出力ym（2の積分状態）
 0 未測定出力yu
 0 測定外乱d
```

# 拡張ヘルプ

!!! details "拡張ヘルプ"
    [`SteadyKalmanFilter`](@ref)の拡張ヘルプは、共分散の調整と`nint_ym`および`nint_u`引数による拡張について詳述しています。デフォルトの拡張スキームは同一であり、すなわち`nint_u=0`および[`default_nint`](@ref)によって計算された`nint_ym`です。コンストラクタは、結果として得られる拡張された[`NonLinModel`](@ref)の可観測性を検証しないことに注意してください。そのような場合、可観測性が維持されることを確認するのはユーザーの責任です。


```
